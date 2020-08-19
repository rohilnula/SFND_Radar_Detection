### Radar Target Generation and Detection:

The project aims at generation and detections of objects using radar. The implmentation is done on MATLAB. Below are the important aspects of the project:

+ Configure the FMCW waveform based on the system requirements.
+ Define the range and velocity of target and simulate its displacement.
+ For the same simulation loop process the transmit and receive signal to determine the beat signal
+ Perform Range FFT on the received signal to determine the Range
+ Towards the end, perform the CFAR processing on the output of 2nd FFT to display the target.

<img src="images/project_layout.png" width="779" height="414" />

# 2D CFAR Implementation:

## Training, Guard Cells and Offset:

Implemeted the 2D CFAR with:
1. Training cells size in Range Tr = 30
2. Training cells size in Doppler Td = 20
3. Guard cells size in Range Gr = 9
4. Guard cells size in Doppler Gd = 9
5. Offset = 13

## Implementation steps for 2D CFAR process:
As given in the directions of the project below are the steps followed:
+ Fixed the size for Training cells and Guard Cells as shown above. 
+ Slide across the matrix and pick the grids that contain training, guard and CUT (Cell Under Test) cells.
+ For each grid calculate the sum of signal levels in all training cells. To sum convert the value from logarithmic to linear using db2pow function.
+ Average the value obtained in the above step by dividing with size of training cells, then convert the value back to logarithmic using pow2db.
+ Add offset to the value calculated in the previous step, which is the required threshold value.
+ Next, compare the signal under CUT against this threshold.
+ If the CUT level > threshold assign it a value of 1, else equate it to 0.

## Steps taken to supress cells at the edges:
For all the cells that fell under CUT in iterating through the process explained above, the value of CUT cells are either replaced with 0 or 1.
So, the edge cells have valued calculated by 2D FFT. Hence, cells with value not either 0 or 1 are replaced with 0, thus supressing them.