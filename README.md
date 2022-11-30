# LANet: A Luminance Attentive Network with Scale Invariance for HDR Image Reconstruction

## Overview 

This is the author's reference implementation of the single-image HDR reconstruction using TensorFlow described in:
"LANet: A Luminance Attentive Network with Scale Invariance for HDR Image Reconstruction"

The network architecture details are shown in "model.py" and the data processing is in "utils.py".

## Testing (on external image, for cuda 10.0

Installation
```
conda create -n LANet python=3.7
conda activate LANet
conda install -c conda-forge cudatoolkit=10.0 cudnn=7.3.1
pip install --upgrade pip
pip3 install tensorflow-gpu==1.13.1 TensorLayer==1.11.0 opencv-python

# Downgrade protobuf (tensorflow issue)
pip3 install protobuf==3.20.*
```

Now, you need to download the checkpoints. Refer to the link below. Store then in ./LANet

Running
```
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$CONDA_PREFIX/lib/
export CUDA_VISIBLE_DEVICES=3
cd LANet
python ./src/main.py --phase test --gpu 0 --checkpoint_dir ./checkpoint_LANet/ --test_dir path_to_input_dir --out_dir path_to_output_dir
```

## Prerequisites

* Python3
* numpy 
* OpenCV >= 3.4
* Tensorflow == 1.13.1
* TensorLayer == 1.11.1


## Usage

### Pretrained model

The pretrained LANet checkpoints can be found in the checkpoints folder on [Google Drive](https://drive.google.com/drive/folders/1cM6hTfCrGplMFSyMmVNz_pC9gqBQAWoo?usp=sharing).
The pretrained panoLANet checkpoints can be found in the checkpoints folder on [Google Drive](https://drive.google.com/drive/folders/1Ex8LzDqwhTgts46ACR0umpKUT1DgYNKQ?usp=sharing).

### Inference

* Run your own images (using our trained LANet):
``` 
cd LANet
python ./src/main.py --phase test --gpu 0 --checkpoint_dir ./checkpoint_LANet/ --test_dir ./test/ --out_dir ./out/
```

* Run your own panoramas (using our trained panoLANet):
``` 
cd panoLANet
python ./src/main.py --phase test --gpu 0 --checkpoint_dir ./checkpoint_panoLANet/ --test_dir ./test/ --out_dir ./out/
```

Parameters and their description:

>```checkpoint_dir```: path to the trained models.<br/>
>```test_dir```: input images directory. This project provides a few sample images.<br/>
>```out_dir```: path to output directory.<br/>
<br/>

See main.py for more settable parameters. 

