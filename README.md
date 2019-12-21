# CSE465.2

Object Detection Project

1 - Gathering images
in my case I use google images to find [chinook] photos , I gather 200 sample

2 - Convert extensoins
convert all images extensoins to xx.jpg , using Format Factory http://www.pcfreetime.com/

3 - Rename all images
go to images directory in my case chinook and type in cmd python renameFiles.py

4 - Label images
using labelImg https://github.com/tzutalin/labelImg unzip labelImg
run cmd and go to labelImg dir

conda install pyqt=5 
pyrcc5 -o resources.py resources.qrc
python labelImg.py

5 - Split images manually randomly
all my samples = 200 ,130 for train ,70 for test

6 - Installing TensorFlow-GPU
pip install --upgrade tensorflow-gpu

7 - Creat virtual environment
conda create -n tensorflow1 pip python=3.5 
activate tensorflow1 
pip install --ignore-installed --upgrade tensorflow-gpu

other necessary packages

(tensorflow1) C:\> conda install -c anaconda protobuf 
(tensorflow1) C:\> pip install pillow 
(tensorflow1) C:\> pip install lxml 
(tensorflow1) C:\> pip install Cython 
(tensorflow1) C:\> pip install jupyter 
(tensorflow1) C:\> pip install matplotlib 
(tensorflow1) C:\> pip install pandas 
(tensorflow1) C:\> pip install opencv-python 

8 - Download the full TensorFlow object detection repository
https://github.com/tensorflow/models.git

9 - Download faster_rcnn_inception_v2_coco
https://github.com/tensorflow/models/blob/master/research/object_detection/g3doc/detection_model_zoo.md

10 - Download my Repository
https://github.com/seraj94ai/Train-Object-Detection-Classifier.git unzip folder and copy paste in C:\tensorflow1\models\research\object_detection open cmd

cd C:\tensorflow1\models\research\object_detection
mkdir images
mkdir inference_graph
mkdir training

11 - Configure environment variable
Configure PYTHONPATH environment variable

PYTHONPATH variable must be created that points to the directories \models
\models\research
\models\research\slim

NOTE : every time you run your project must add this lines
set PYTHONPATH=C:\tensorflow1\models;C:\tensorflow1\models\research;C:\tensorflow1\models\research\slim
echo %PYTHONPATH%
set PATH=%PATH%;PYTHONPATH
echo %PATH%

12 - Compile Protobufs
Protobuf (Protocol Buffers) libraries must be compiled , it used by TensorFlow to configure model and training parameters Open Anaconda Prompt and go to C:\tensorflow1\models\research

protoc --python_out=. .\object_detection\protos\anchor_generator.proto .\object_detection\protos\argmax_matcher.proto .\object_detection\protos\bipartite_matcher.proto .\object_detection\protos\box_coder.proto .\object_detection\protos\box_predictor.proto .\object_detection\protos\eval.proto .\object_detection\protos\faster_rcnn.proto .\object_detection\protos\faster_rcnn_box_coder.proto .\object_detection\protos\grid_anchor_generator.proto .\object_detection\protos\hyperparams.proto .\object_detection\protos\image_resizer.proto .\object_detection\protos\input_reader.proto .\object_detection\protos\losses.proto .\object_detection\protos\matcher.proto .\object_detection\protos\mean_stddev_box_coder.proto .\object_detection\protos\model.proto .\object_detection\protos\optimizer.proto .\object_detection\protos\pipeline.proto .\object_detection\protos\post_processing.proto .\object_detection\protos\preprocessor.proto .\object_detection\protos\region_similarity_calculator.proto .\object_detection\protos\square_box_coder.proto .\object_detection\protos\ssd.proto .\object_detection\protos\ssd_anchor_generator.proto .\object_detection\protos\string_int_label_map.proto .\object_detection\protos\train.proto .\object_detection\protos\keypoint_box_coder.proto .\object_detection\protos\multiscale_anchor_generator.proto .\object_detection\protos\graph_rewriter.proto

(tensorflow1) C:\tensorflow1\models\research> python setup.py build
(tensorflow1) C:\tensorflow1\models\research> python setup.py install

13 - Test TensorFlow setup
Test TensorFlow setup to verify it works (tensorflow1) C:\tensorflow1\models\research\object_detection> jupyter notebook object_detection_tutorial.ipynb

14 - Generate Training Data
TFRecords is an input data to the TensorFlow training model creat .csv files from .xml files

cd C:\tensorflow1\models\research\object_detection
python xml_to_csv.py
