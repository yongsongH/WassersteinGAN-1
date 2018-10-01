# Wasserstein GAN (with Gradient Penalty) 
[![dep1](https://img.shields.io/badge/Tensorflow-1.3+-blue.svg)](https://www.tensorflow.org/)
[![license](https://img.shields.io/badge/License-MIT-brightgreen.svg)](https://github.com/asahi417/WassersteinGAN/blob/master/LICENSE)

Tensorflow implementation of [Wasserstein GAN](https://arxiv.org/pdf/1701.07875.pdf) with [gradient penalty](https://papers.nips.cc/paper/7159-improved-training-of-wasserstein-gans.pdf)
and [DCGAN](https://arxiv.org/pdf/1511.06434.pdf).
Properties are summalized as below

- Tested by [CelebA dataset](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html) 
- Data is encoded as TFRecord format


# How to use it ?
Clone the repository

```
git clone https://github.com/asahi417/WassersteinGAN
cd WassersteinGAN
pip install .
mkdir datasets
```

CelebA dataset need to be downloaded from [here](http://mmlab.ie.cuhk.edu.hk/projects/CelebA.html), and be located below the directory `datasets`, so the data directory should be seems like

```
WassersteinGAN/datasets/celeba/img/img_align_celeba
```

***TFRecord***

To produce TFRecord file, 

```
python bin/build_tfrecord.py --data celeba -r 64 -c 108

optional arguments:
    -c [CROP], --crop [CROP] Each image will be center cropped by this integer.
    -r [RESIZE], --resize [RESIZE] Each image will be resized by this integer.
``` 

***Train Model***

```
python bin/train.py -m [MODEL] -e [EPOCH] -c [CROP] -r [RESIZE] --data [DATA]

optional arguments:
  -m [MODEL], --model [MODEL] `dcgan` or `wgan`
  -e [EPOCH], --epoch [EPOCH] Epoch.
  -c [CROP], --crop [CROP]
  -r [RESIZE], --resize [RESIZE]
```

Hyperparameters are [here](./bin/hyperparameter).

***Visualization***

```
usage: generate_img.py -m [MODEL] -v [VERSION] -c [CROP] -r [RESIZE] --data [DATA]

optional arguments:
  -m [MODEL], --model [MODEL] `dcgan` or `wgan`
  -v [VERSION], --version [VERSION] version of checkpoint
  -c [CROP], --crop [CROP]
  -r [RESIZE], --resize [RESIZE]
```

# Generated Images


