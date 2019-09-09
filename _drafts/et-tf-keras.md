---
layout: post
title: logging->Keras 调 Tensorflow 完成 mnist 探索
description: ~ 社区活动, 值得掺合;-)
author: zoomq
categories: Events
tags:  gdg event meetup
---



<!--more-->



༄  conda info

     active environment : leo373
    active env location : /Users/zoomq/miniconda3/envs/leo373
            shell level : 1
       user config file : /Users/zoomq/.condarc
 populated config files : /Users/zoomq/.condarc
          conda version : 4.6.14
    conda-build version : not installed
         python version : 3.7.3.final.0
       base environment : /Users/zoomq/miniconda3  (writable)
           channel URLs : https://repo.anaconda.com/pkgs/main/osx-64
                          https://repo.anaconda.com/pkgs/main/noarch
                          https://repo.anaconda.com/pkgs/free/osx-64
                          https://repo.anaconda.com/pkgs/free/noarch
                          https://repo.anaconda.com/pkgs/r/osx-64
                          https://repo.anaconda.com/pkgs/r/noarch
          package cache : /Users/zoomq/miniconda3/pkgs
                          /Users/zoomq/.conda/pkgs
       envs directories : /Users/zoomq/miniconda3/envs
                          /Users/zoomq/.conda/envs
               platform : osx-64
             user-agent : conda/4.6.14 requests/2.21.0 CPython/3.7.3 Darwin/16.7.0 OSX/10.12.6
                UID:GID : 501:20
             netrc file : /Users/zoomq/.netrc
           offline mode : False



༄  conda create --clone base --name keras


༄  conda env list
# conda environments:
#
base                     /Users/zoomq/miniconda3
keras                 *  /Users/zoomq/miniconda3/envs/keras
leo373                   /Users/zoomq/miniconda3/envs/leo373


༼conda: keras༽/opt/data/Sites/org.zhgdg/TFUG.ZH/keras.k༽

༄  conda list
# packages in environment at /Users/zoomq/miniconda3/envs/keras:
#
# Name                    Version                   Build  Channel
asn1crypto                0.24.0                   py37_0
ca-certificates           2019.1.23                     0
certifi                   2019.3.9                 py37_0
cffi                      1.12.2           py37hb5b8e2f_1
chardet                   3.0.4                    py37_1
cryptography              2.6.1            py37ha12b0ac_0
idna                      2.8                      py37_0
libcxx                    4.0.1                hcfea43d_1
libcxxabi                 4.0.1                hcfea43d_1
libedit                   3.1.20181209         hb402a30_0
libffi                    3.2.1                h475c297_4
ncurses                   6.1                  h0a44026_1
openssl                   1.1.1b               h1de35cc_1
pip                       19.0.3                   py37_0
pycosat                   0.6.3            py37h1de35cc_0
pycparser                 2.19                     py37_0
pyopenssl                 19.0.0                   py37_0
pysocks                   1.6.8                    py37_0
python                    3.7.3                h359304d_0
python.app                2                        py37_9
readline                  7.0                  h1de35cc_5
requests                  2.21.0                   py37_0
ruamel_yaml               0.15.46          py37h1de35cc_0
setuptools                41.0.0                   py37_0
six                       1.12.0                   py37_0
sqlite                    3.27.2               ha441bb4_0
tk                        8.6.8                ha441bb4_0
urllib3                   1.24.1                   py37_0
wheel                     0.33.1                   py37_0
xz                        5.2.4                h1de35cc_4
yaml                      0.1.7                hc338f04_2
zlib                      1.2.11               h1de35cc_3


Step-by-step Guide to Install TensorFlow 2 - Chitta Ranjan - Medium https://medium.com/@cran2367/install-and-setup-tensorflow-2-0-2c4914b9a265





>    仅支持 CPU 的 TensorFlow 版本，请输入以下命令：

pip install --ignore-installed --upgrade tensorflow




༄  pip search tensorflow
tensorflow (1.14.0)                                      - TensorFlow is an open source machine learning framework for everyone.
tensorflow-qndex (0.0.22)                                - tensorflow-qnd x tensorflow-extenteten
tensorflow-ops (0.0.0)                                   - tensorflow-ops
tensorflow-estimator (1.14.0)                            - TensorFlow Estimator.
mesh-tensorflow (0.0.5)                                  - Mesh TensorFlow
...



༄  pip install tensorflow
Looking in indexes: https://mirrors.aliyun.com/pypi/simple/
Collecting tensorflow
  Downloading https://mirrors.aliyun.com/pypi/packages/ed/11/037887c5cbac5af3124050fb6348e67caa038734cc9673b11c31c8939072/tensorflow-1.14.0-cp37-cp37m-macosx_10_11_x86_64.whl (105.8MB)
    11% |███▋                            | 11.9MB 11.8MB/s eta 0:00:08

...


Building wheels for collected packages: absl-py, gast, wrapt, termcolor
  Building wheel for absl-py (setup.py) ... done
  Stored in directory: /Users/zoomq/Library/Caches/pip/wheels/a6/f8/c3/8fd5ed9314858d27abc81a01c71f7c192cb22c049862a9b9b8
  Building wheel for gast (setup.py) ... done
  Stored in directory: /Users/zoomq/Library/Caches/pip/wheels/84/e1/af/35de1442e204ec87ba0b357286baa19bc44127af2ffff7ad6e
  Building wheel for wrapt (setup.py) ... done
  Stored in directory: /Users/zoomq/Library/Caches/pip/wheels/8d/2f/70/a7eb77f64901f105bee1ed46a036004751c6eeada6f73bad3b
  Building wheel for termcolor (setup.py) ... done
  Stored in directory: /Users/zoomq/Library/Caches/pip/wheels/38/14/af/ba98b01b9d03d7b61142df3389b830153cfdb2f1846ed7e25b
Successfully built absl-py gast wrapt termcolor
Installing collected packages: google-pasta, absl-py, astor, numpy, keras-preprocessing, protobuf, markdown, werkzeug, grpcio, tensorboard, h5py, keras-applications, gast, wrapt, termcolor, tensorflow-estimator, tensorflow
Successfully installed absl-py-0.8.0 astor-0.8.0 gast-0.2.2 google-pasta-0.1.7 grpcio-1.23.0 h5py-2.9.0 keras-applications-1.0.8 keras-preprocessing-1.1.0 markdown-3.1.1 numpy-1.17.1 protobuf-3.9.1 tensorboard-1.14.0 tensorflow-1.14.0 tensorflow-estimator-1.14.0 termcolor-1.1.0 werkzeug-0.15.6 wrapt-1.11.2




༄  pip install jupyter
Looking in indexes: https://mirrors.aliyun.com/pypi/simple/
Collecting jupyter
  Downloading https://mirrors.aliyun.com/pypi/packages/83/df/0f5dd132200728a86190397e1ea87cd76244e42d39ec5e88efd25b2abd7e/jupyter-1.0.0-py2.py3-none-any.whl
Collecting ipywidgets (from jupyter)
  Downloading https://mirrors.aliyun.com/pypi/packages/56/a0/dbcf5881bb2f51e8db678211907f16ea0a182b232c591a6d6f276985ca95/ipywidgets-7.5.1-py2.py3-none-any.whl (121kB)
    100% |████████████████████████████████| 122kB 2.0MB/s
Collecting notebook (from jupyter)
  Downloading https://mirrors.aliyun.com/pypi/packages/f3/a1/1e07cedcb554408fefe4a7d32b2a041c86517167aec6ca8251c808ef6c1e/notebook-6.0.1-py3-none-any.whl (9.0MB)
    100% |████████████████████████████████| 9.0MB 7.3MB/s

    ...


  Stored in directory: /Users/zoomq/Library/Caches/pip/wheels/08/d0/94/da1a65bb72f0faa17cda1a7c977e5440ccad23f5b9054c23a9
Successfully built prometheus-client tornado pandocfilters backcall pyrsistent
Installing collected packages: ipython-genutils, decorator, traitlets, prometheus-client, ptyprocess, tornado, terminado, MarkupSafe, jinja2, pyrsistent, attrs, jsonschema, jupyter-core, nbformat, pyzmq, python-dateutil, jupyter-client, webencodings, bleach, pygments, pandocfilters, defusedxml, testpath, mistune, entrypoints, nbconvert, Send2Trash, pickleshare, parso, jedi, backcall, pexpect, appnope, wcwidth, prompt-toolkit, ipython, ipykernel, notebook, widgetsnbextension, ipywidgets, jupyter-console, qtconsole, jupyter
Successfully installed MarkupSafe-1.1.1 Send2Trash-1.5.0 appnope-0.1.0 attrs-19.1.0 backcall-0.1.0 bleach-3.1.0 decorator-4.4.0 defusedxml-0.6.0 entrypoints-0.3 ipykernel-5.1.2 ipython-7.8.0 ipython-genutils-0.2.0 ipywidgets-7.5.1 jedi-0.15.1 jinja2-2.10.1 jsonschema-3.0.2 jupyter-1.0.0 jupyter-client-5.3.1 jupyter-console-6.0.0 jupyter-core-4.5.0 mistune-0.8.4 nbconvert-5.6.0 nbformat-4.4.0 notebook-6.0.1 pandocfilters-1.4.2 parso-0.5.1 pexpect-4.7.0 pickleshare-0.7.5 prometheus-client-0.7.1 prompt-toolkit-2.0.9 ptyprocess-0.6.0 pygments-2.4.2 pyrsistent-0.15.4 python-dateutil-2.8.0 pyzmq-18.1.0 qtconsole-4.5.5 terminado-0.8.2 testpath-0.4.2 tornado-6.0.3 traitlets-4.3.2 wcwidth-0.1.7 webencodings-0.5.1 widgetsnbextension-3.5.1



༄  ipython
Python 3.7.3 (default, Mar 27 2019, 16:54:48)
Type 'copyright', 'credits' or 'license' for more information
IPython 7.8.0 -- An enhanced Interactive Python. Type '?' for help.

In [1]: import tensorflow as tf
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:516: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint8 = np.dtype([("qint8", np.int8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:517: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint8 = np.dtype([("quint8", np.uint8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:518: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint16 = np.dtype([("qint16", np.int16, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:519: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint16 = np.dtype([("quint16", np.uint16, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:520: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint32 = np.dtype([("qint32", np.int32, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:525: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  np_resource = np.dtype([("resource", np.ubyte, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:541: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint8 = np.dtype([("qint8", np.int8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:542: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint8 = np.dtype([("quint8", np.uint8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:543: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint16 = np.dtype([("qint16", np.int16, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:544: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint16 = np.dtype([("quint16", np.uint16, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:545: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint32 = np.dtype([("qint32", np.int32, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:550: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  np_resource = np.dtype([("resource", np.ubyte, 1)])

In [2]: hello = tf.constant('Hello, TensorFlow!')

In [3]: sess = tf.Session()
2019-09-06 21:30:14.716974: I tensorflow/core/platform/cpu_feature_guard.cc:142] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA

In [4]: print(sess.run(hello))
b'Hello, TensorFlow!'

In [5]:


...





༄  conda update --all
Collecting package metadata: done
Solving environment: done


==> WARNING: A newer version of conda exists. <==
  current version: 4.6.14
  latest version: 4.7.11

Please update conda by running

    $ conda update -n base -c defaults conda



## Package Plan ##

  environment location: /Users/zoomq/miniconda3/envs/keras


The following packages will be downloaded:

    package                    |            build
    ---------------------------|-----------------
    ca-certificates-2019.5.15  |                1         133 KB
    certifi-2019.6.16          |           py37_1         155 KB
    cffi-1.12.3                |   py37hb5b8e2f_0         214 KB
    chardet-3.0.4              |        py37_1003         173 KB
    cryptography-2.7           |   py37ha12b0ac_0         571 KB
    pip-19.2.2                 |           py37_0         1.9 MB
    pysocks-1.7.0              |           py37_0          29 KB
    python-3.7.4               |       h359304d_1        21.6 MB
    requests-2.22.0            |           py37_0          89 KB
    setuptools-41.0.1          |           py37_0         635 KB
    sqlite-3.29.0              |       ha441bb4_0         2.4 MB
    urllib3-1.24.2             |           py37_0         152 KB
    wheel-0.33.4               |           py37_0          39 KB
    ------------------------------------------------------------
                                           Total:        28.0 MB

The following packages will be UPDATED:

  ca-certificates                               2019.1.23-0 --> 2019.5.15-1
  certifi                                   2019.3.9-py37_0 --> 2019.6.16-py37_1
  cffi                                1.12.2-py37hb5b8e2f_1 --> 1.12.3-py37hb5b8e2f_0
  chardet                                      3.0.4-py37_1 --> 3.0.4-py37_1003
  cryptography                         2.6.1-py37ha12b0ac_0 --> 2.7-py37ha12b0ac_0
  openssl                                 1.1.1b-h1de35cc_1 --> 1.1.1c-h1de35cc_1
  pip                                         19.0.3-py37_0 --> 19.2.2-py37_0
  pysocks                                      1.6.8-py37_0 --> 1.7.0-py37_0
  python                                   3.7.3-h359304d_0 --> 3.7.4-h359304d_1
  requests                                    2.21.0-py37_0 --> 2.22.0-py37_0
  setuptools                                  41.0.0-py37_0 --> 41.0.1-py37_0
  sqlite                                  3.27.2-ha441bb4_0 --> 3.29.0-ha441bb4_0
  urllib3                                     1.24.1-py37_0 --> 1.24.2-py37_0
  wheel                                       0.33.1-py37_0 --> 0.33.4-py37_0


Proceed ([y]/n)?

...

python-3.7.4         | 21.6 MB   | ################################################################################################### | 100%
Preparing transaction: done
Verifying transaction: done
Executing transaction: done




༄  pip install keras
Looking in indexes: https://mirrors.aliyun.com/pypi/simple/
Collecting keras
  Downloading https://mirrors.aliyun.com/pypi/packages/f8/ba/2d058dcf1b85b9c212cc58264c98a4a7dd92c989b798823cc5690d062bb2/Keras-2.2.5-py2.py3-none-any.whl (336kB)
     |████████████████████████████████| 337kB 1.2MB/s
Collecting pyyaml (from keras)

...


Building wheels for collected packages: pyyaml
  Building wheel for pyyaml (setup.py) ... done
  Created wheel for pyyaml: filename=PyYAML-5.1.2-cp37-cp37m-macosx_10_9_x86_64.whl size=148974 sha256=836b126e9463337713f0a0df43f0e9e5770d75275852f938c329108fc218b683
  Stored in directory: /Users/zoomq/Library/Caches/pip/wheels/f1/62/c9/f61bd2c2ae2f87b452a27f973b222d0b18626e3354aa150ca2
Successfully built pyyaml
Installing collected packages: pyyaml, scipy, keras
Successfully installed keras-2.2.5 pyyaml-5.1.2 scipy-1.3.1



## mnist_cnn
> 基本 训练

༄  python mnist_cnn.py
Using TensorFlow backend.
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:516: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint8 = np.dtype([("qint8", np.int8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:517: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint8 = np.dtype([("quint8", np.uint8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:518: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint16 = np.dtype([("qint16", np.int16, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:519: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint16 = np.dtype([("quint16", np.uint16, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:520: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint32 = np.dtype([("qint32", np.int32, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:525: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  np_resource = np.dtype([("resource", np.ubyte, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:541: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint8 = np.dtype([("qint8", np.int8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:542: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint8 = np.dtype([("quint8", np.uint8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:543: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint16 = np.dtype([("qint16", np.int16, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:544: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint16 = np.dtype([("quint16", np.uint16, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:545: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint32 = np.dtype([("qint32", np.int32, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorboard/compat/tensorflow_stub/dtypes.py:550: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  np_resource = np.dtype([("resource", np.ubyte, 1)])
Downloading data from https://s3.amazonaws.com/img-datasets/mnist.npz
  409600/11490434 [>.............................] - ETA: 5:39

...




太慢, 通过国外主机直接下载


MNIST手写数字识别可以理解为深度学习领域的HelloWorld，mnist数据是手写数字的数据集合，训练集规模为60000，测试集为10000
更多详细内容可以查看官网 http://yann.lecun.com/exdb/mnist/



import numpy as np
# 内置load_data() 多次加载数据都是失败 于是下载数据后 自定义方法
def locload_data(path="./mnist.npz"):
    f = np.load(path)
    x_train, y_train = f['x_train'], f['y_train']
    x_test, y_test = f['x_test'], f['y_test']
    f.close()
    return (x_train, y_train), (x_test, y_test)


# the data, split between train and test sets
#(x_train, y_train), (x_test, y_test) = mnist.load_data()
(x_train, y_train), (x_test, y_test) = locload_data()

...



༄  python cnn_mnist.py
Using TensorFlow backend.
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:516: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_qint8 = np.dtype([("qint8", np.int8, 1)])
/Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/tensorflow/python/framework/dtypes.py:517: FutureWarning: Passing (type, 1) or '1type' as a synonym of type is deprecated; in a future version of numpy, it will be understood as (type, (1,)) / '(1,)type'.
  _np_quint8 = np.dtype([("quint8", np.uint8, 1)])

  ...


x_train shape: (60000, 28, 28, 1)
60000 train samples
10000 test samples
WARNING:tensorflow:From /Users/zoomq/miniconda3/envs/keras/lib/python3.7/site-packages/keras/backend/tensorflow_backend.py:66: The name tf.get_default_graph is deprecated. Please use tf.compat.v1.get_default_graph inst

...


2019-09-06 21:52:26.247729: I tensorflow/core/platform/cpu_feature_guard.cc:142] Your CPU supports instructions that this TensorFlow binary was not compiled to use: AVX2 FMA
60000/60000 [==============================] - 245s 4ms/step - loss: 0.2695 - acc: 0.9168 - val_loss: 0.0574 - val_acc: 0.9817
Epoch 2/12
60000/60000 [==============================] - 202s 3ms/step - loss: 0.0910 - acc: 0.9734 - val_loss: 0.0386 - val_acc: 0.9869
Epoch 3/12
60000/60000 [==============================] - 188s 3ms/step - loss: 0.0666 - acc: 0.9800 - val_loss: 0.0343 - val_acc: 0.9886
Epoch 4/12
60000/60000 [==============================] - 164s 3ms/step - loss: 0.0565 - acc: 0.9830 - val_loss: 0.0317 - val_acc: 0.9895
Epoch 5/12
60000/60000 [==============================] - 180s 3ms/step - loss: 0.0487 - acc: 0.9858 - val_loss: 0.0293 - val_acc: 0.9897
Epoch 6/12
60000/60000 [==============================] - 177s 3ms/step - loss: 0.0426 - acc: 0.9876 - val_loss: 0.0301 - val_acc: 0.9900
Epoch 7/12
60000/60000 [==============================] - 193s 3ms/step - loss: 0.0384 - acc: 0.9883 - val_loss: 0.0266 - val_acc: 0.9912
Epoch 8/12
60000/60000 [==============================] - 200s 3ms/step - loss: 0.0351 - acc: 0.9893 - val_loss: 0.0331 - val_acc: 0.9896
Epoch 9/12
60000/60000 [==============================] - 231s 4ms/step - loss: 0.0321 - acc: 0.9900 - val_loss: 0.0298 - val_acc: 0.9906
Epoch 10/12
60000/60000 [==============================] - 229s 4ms/step - loss: 0.0300 - acc: 0.9910 - val_loss: 0.0272 - val_acc: 0.9913
Epoch 11/12
60000/60000 [==============================] - 226s 4ms/step - loss: 0.0290 - acc: 0.9910 - val_loss: 0.0287 - val_acc: 0.9914
Epoch 12/12
60000/60000 [==============================] - 229s 4ms/step - loss: 0.0268 - acc: 0.9917 - val_loss: 0.0261 - val_acc: 0.9919
Test loss: 0.026105740693741244
Test accuracy: 0.9919


## refer.


- [面向机器学习初学者的 MNIST 初级教程](http://tensorfly.cn/tfdoc/tutorials/mnist_beginners.html)
- [Handwritten Digit Recognition using Deep Learning, Keras and Python – Gogul Ilango](https://gogul09.github.io/software/digits-recognition-mlp)
    + [Dwijraj/Hand-Written-Digit-Recognition: This is a repository with various classifier written in jupyter notebook that works on hand written digits images.](https://github.com/Dwijraj/Hand-Written-Digit-Recognition)
    + [keras/mnist_cnn.py at master · keras-team/keras](https://github.com/keras-team/keras/blob/master/examples/mnist_cnn.py)
    + [kerasのmnistのサンプルを読んでみる - Qiita](https://qiita.com/ash8h/items/29e24fc617b832fba136)
- [基于Keras+CNN的MNIST数据集手写数字分类 - 简书](https://www.jianshu.com/p/3a8b310227e6)
    + [Keras_mnist学习 - 简书](https://www.jianshu.com/p/769fb8d6cab0)
    + [keras实现mnist数据集手写数字识别 - 胡卫雄 - 博客园](https://www.cnblogs.com/ncuhwxiong/p/9774515.html)
    + [深度学习：基于keras的mnist手写数字识别 | AI柠檬](https://blog.ailemon.me/2018/05/11/deep-learning-mnist-handwritten-digit-recognition-by-keras/)




## logging

> NN 3762


