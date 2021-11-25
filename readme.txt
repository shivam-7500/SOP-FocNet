This repository contains the implementation of the FOCNet.
Steps to setup the project:
1. Clone the project repo.
2. Download the MatcovNet 1.0-beta25. (https://www.vlfeat.org/matconvnet/) 
3. Place the downloaded MatcovNet folder inside the main FocNet folder.
4. Open the FocNet folder in the matlab.
5. Setup.m - This file setups the matcovnet toolbox implementing Convolutional Neural Networks (CNNs) for computer vision applications.
	5.1 Run these commands in matlab mex -setup mex -setup C++. Try to run Setup.m.
	5.2 In case of error comment out the line 3 (line 3 vl_compilenn('enableGpu', true))
	5.3 In case of error related to cl_path. Follow the following steps.
		1. You can find the cl file in the program files where Microsoft Studio is installed. (For eg: 'C:\Program Files (x86)\Microsoft Visual Studio\2019\Community\VC\Tools\MSVC\14.29.30037\bin\Hostx64\x86\cl.exe)
		2. Copy this path and paste it in the vl_compilenn.m file at line 426. (cl_path = "The path you copied")
	5.4 Now run the setup.m file 
6. Download test and train sets. I have used BSDS300 dataset.
	6.1 Create Train_Set folder in the main FocNet directory and place the testing images inside this folder.
	6.1 Create a testsets folder in the main FocNet directory. Place the test set folder inside this folder which contains all the test set images.
7. Run the Demo_Train_FracDNN_DAG file.
7. In the Demo_Test_FracDNN_DAG change the setTestCur variable to the name of the test image folder (line 10)
8. Run the Demo_Test_FracDNN_DAG to get the predictions.

Some additional things required
1. Parallel Computing Toolbox
2. Image Processing Toolbox

Some error you might face
In case you see some error related to GPU try commenting out those lines from the code and try to run it again.

File and their use
generatepatches.m = This file generates batches from the training dataset. The batch size,stride and other parameters are specified in this file. All the data augmentation also takes place in this file.
FracDNN.m file = This files contains the complete architecture of the FocNet.
setup.m = This file is used to setup the matcovnet.
Demo_Train_FracDCNN_DAG.m = This file is used for training the model using your dataset.
Demo_Test_FracDCNN_DAG.m = This file is used for testing the model on your dataset.
FracDCNN_train_dag.m = Demonstrates training a CNN using the DagNN wrapper (DagNN is a CNN wrapper alternative to SimpleNN. It is object oriented and allows constructing networks with a directed acyclic graph (DAG) topology.)