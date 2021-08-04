# Environment Settings   
<font color= #DC143C> OS:Windows 10</font>         

## Anaconda  
I will use anaconda to manage every package, which it really do well in.    
#### Download     
[anaconda](https://www.anaconda.com/distribution "anaconda download")   
![click the green botton to download](D:/Desktop/create/picture/1.png)
#### Configuration    
![all check](D:/Desktop/create/picture/2.png)
![skip and finish](D:/Desktop/create/picture/3.png)

![install confirmation](D:/Desktop/create/picture/4.png)
- wins+R 
- input "cmd"
- input "conda list"
#### Create Environment
Use conda to create a new environment,named as tf114, specify the python version as 3.7.
```
conda create -n tf114 python=3.7
```
Choose yes in every step.
Then turn into this environment.
```
conda activate tf114
```



#### <font color=#00CED1> Change the resource to accelerate</font>
**conda** 
```
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/conda-forge/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/free/
conda config --add channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/pkgs/main/
conda config --append channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/fastai/
conda config --append channels https://mirrors.tuna.tsinghua.edu.cn/anaconda/cloud/bioconda/
 
conda config --set show_channel_urls yes
```
**pip** 
```
pip config set global.index-url https://pypi.tuna.tsinghua.edu.cn/simple
```
> The reminded "conda" and "pip" are tools to manage python packages. 
> **Conda command (env_name was the name of environment)：**
> - look over all the conda environment: `conda env list`
> - create new conda environment(env_name is its name, you can costomize it):`conda create -n env_name`
> - activate conda environment:`conda activate env_name`
> - exit the current conda environment(back to base/root):`conda deactivate`
> - install python packages:`conda install numpy`
> - uninstall python packages:`conda uninstall numpy`
> - list out all the installed packages:`conda list -n env_name`  
> 
> **Pip command（take numpy as an example）：**
> - install packages:`pip install numpy`
> - uninstall packages:`pip uninstall numpy`
> - upgrade packages:`pip install --upgrade numpy`
> - list out all theinstalled packages：`pip list`
> 
> **Because we download and install conda and pip through the internet, so the computer should keep in connection throughout the whole process.**   
> **If you see error with <font color= #DC143C> “HTTP 000” </font>, there are something wrong in you network.**    
> **There are two probabilitis:**
> 1.the computer don't connect the network 
> 2.the connection is not stable
> You can check the local network. If it is okay, maybe it is not stable, and you can try more.

-----

## Tensorflow     
<font color= #DC143C> Tensorflow = 1.14.0   
CUDA = 10.0
cudnn = 7.4 </font> 
！！！We should focus on the version, because only correct correspondence can lead in perfect operatoring state.
![version information](https://img-blog.csdnimg.cn/20210105181338479.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3hpYW9zb25nc2hpbmU=,size_16,color_FFFFFF,t_70)
#### CUDA   
1.Download
![choose 10.0](D:/Desktop/create/picture/5.png)
![download](D:/Desktop/create/picture/6.png)
2.Install
There will be twice directory settings:
<font color=#DC143C> The Path Must Be Different! </font>
- temporary decompression directory
- setting installation directory
  If they are same, you won't find installation directory!
some steps like this:
![](https://img-blog.csdnimg.cn/20181115145139807.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzIzNjE5NDA5,size_16,color_FFFFFF,t_70)
![](https://img-blog.csdnimg.cn/20181119113857442.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzIzNjE5NDA5,size_16,color_FFFFFF,t_70)
![](https://img-blog.csdnimg.cn/20181119113916150.png?x-oss-process=image/watermark,type_ZmFuZ3poZW5naGVpdGk,shadow_10,text_aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3NpbmF0XzIzNjE5NDA5,size_16,color_FFFFFF,t_70)
3.check
![CUDA verify](D:/Desktop/create/picture/15.png)
![CUPTI verify](D:/Desktop/create/picture/16.png)
Open the command line and input `nvcc -V`.
If it happens like the picture, you have succeeded in installing CUDA.
![CUDA test](D:/Desktop/create/picture/14.png)

#### cudnn
1.Download  
![choose 7.4](D:/Desktop/create/picture/7.png)
2.Install
We just need to decompress it in the directory of <font color= #DC143C>CUDA</font>, and rename it as <font color= #DC143C>cudnn</font>.
![location](D:/Desktop/create/picture/8.png)
3.check
![cudnn verify](D:/Desktop/create/picture/17.png)

#### Tensorflow
We choose the GPU version, because it has so many advantages like rapid running speed
```
pip install tensorflow-gpu==1.14.0
```

#### Condiguration 
![](D:/Desktop/create/picture/9.png)
![](D:/Desktop/create/picture/10.png)
- click "New" to add items
- click "Move Up" to make sure the new items are on the top
![add CUPTI path](D:/Desktop/create/picture/11.png)
![add cudnn path](D:/Desktop/create/picture/12.png)
![PAth variate verify](D:/Desktop/create/picture/13.png)


#### Test    
**steps:**
1.open the command line:`Wins+R`,then input "cmd"
2.activate the environment:`conda activate tf114`
3.access to python compiling environment:`python`
4.test:
input
```
import tensorflow as tf
print(tf.__version__)   #TensorFlow version information 
print(tf.test.is_gpu_available())   #TensorFlow GPU supportion
exit()  #exit the python command line
```



-----

> **Reference Data**    
> 1.Courses from Long Quliang
> 2.[Grammar Specification of Markdown](https://blog.csdn.net/china_jeffery/article/details/78997984?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162803947416780269869701%2522%252C%2522scm%2522%253A%252220140713.130102334.pc%255Fblog.%2522%257D&request_id=162803947416780269869701&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~first_rank_v2~rank_v29-6-78997984.first_rank_v2_pc_rank_v29&utm_term=markdown&spm=1018.2226.3001.4187) 
> 3.[Install CUDA and cudnn](https://blog.csdn.net/sinat_23619409/article/details/84202651?ops_request_misc=%257B%2522request%255Fid%2522%253A%2522162799457316780274125098%2522%252C%2522scm%2522%253A%252220140713.130102334..%2522%257D&request_id=162799457316780274125098&biz_id=0&utm_medium=distribute.pc_search_result.none-task-blog-2~all~sobaiduend~default-1-84202651.first_rank_v2_pc_rank_v29&utm_term=cuda+cudnn%E5%AE%89%E8%A3%85&spm=1018.2226.3001.4187)
> 4.[Environment Configuration](https://xiaosongshine.blog.csdn.net/article/details/112249592)
> 5.