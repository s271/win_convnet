win_convnet
===========

Port to windows x64 of Alex Krizhevsky's cuda-convnet. Original project and documentation at http://code.google.com/p/cuda-convnet/

Requirements:
--------------

NVIDIA videocad with cuda compute capability 2.0 or better


Windows x64


Cuda SDK 4.2 (will not work for 5.0, for 5.0 port look to original project commentaries or Wyvernbai blog http://www.asiteof.me/archives/50)

Visual Studio 2008 or later with x64 support(x64 is not installed by defult in VS, may require installation update).

Python 2.7 64bit; Neither Python 3.*, nor Python compiled for 32 bits will not work

NumPy package for 64bit Python
NumPy for window and 64bit python included in Anaconda package and WinPython package. Pythonxy will not work - it's only 32 bit

Recommended:
------------

Install WinPython or Anaconda for both 64bit Python and NumPy

Installation:
-------------

1. Make shure that you have PYTHONPATH enviromental variable set only to your 64 bit Python folder. If it set to other folder(s) you should replace $(PYTHONPATH) in the project settings in C/C++ and linker to absolute directory of 64bit  python.

2. create folder in (NVIDIA SDK)\C\src folder and create repository there
  (for example E:\ProgramData\NVIDIA Corporation\NVIDIA GPU Computing SDK 4.2\C\src\convnet) and pull

3. unpack win_convnet\dlls.zip into win_convnet folder

4. build project pyconvnet for x64 (preferably Release), it should produce pyconvnet.pyd (dll for python) in win_convnet folder

5. run synthetic test from https://code.google.com/p/cuda-convnet/wiki/CheckingGradients :

  python convnet.py --layer-def=./example-layers/layers.gc.cfg --layer-params=./example-layers/layer-params.gc.cfg --data-provider=dummy-cn-192 --check-grads=1

  Depending on your videocard some tests may fail, but majority should almoste always pass.
  
6. Download real data from http://www.cs.toronto.edu/~kriz/cifar-10-py-colmajor.tar.gz and run training on them, as described at 
https://code.google.com/p/cuda-convnet/wiki/Methodology



While building this project I've followed exellent instructions by Yalong Bai(Wyvernbai)from  http://www.asiteof.me/archives/50 and used his precompiled dlls, with some changes (cuda 4.2 instead of 5.2)
