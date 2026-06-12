---
title: "[SOLVED] has anybody gotten to install scilab 5.03 on ubuntu"
date: 2008-11-17
forum: Education &amp; Science
---

### Post by bigbrovar on 2008-11-17
I tried building from soorce but met with some serious dependency errors. the version in the repo is very old and the is no packaged deb for ubuntu yet.

---

### Post by bigbrovar on 2008-11-18
there say if u want something done you'd better do it your self.. since they was no deb package for the latest scilab 5.0.3. i had no choice than to build one from source. it wasnt easy hunting down the needed dependency many of which are not availablein the hardy repository. i had to download the from online from the intrepid repo . here was what i did 



first download the latest scilab 5.0.3 

```
wget http://www.scilab.org/download/5.0.3/scilab-5.0.3-src.tar.gz
```

mv it to your home directory

```
mv scilab-5.0.3-src.tar.gz $HOME
```

then we install the scilab dependencies that are available in that hardy repository

```
sudo apt-get build-dep scilab
```
```
sudo apt-get install liblaf-plugin-java libjgoodies-looks-java scilab-doc ant sun-java5-jdk  
```

once that is done
time to download and install the external dependencies that are not available in hardy repo to make things easy we create a directory called dependencies 

```
mkdir dependencies
```

now we enter into the dependencies directory we just created
 
```
cd dependencies
```

then we download the required dependencies 

**libflexdock-jni**
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/libf/libflexdock-java/libflexdock-jni_0.5.1-dfsg1-4_i386.deb
```


**libflexdock-java-doc**
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/libf/libflexdock-java/libflexdock-java-doc_0.5.1-dfsg1-4_all.deb
```


**libflexdock-java-demo**
**wget  [http://mirrors.kernel.org/ubuntu/pool/universe/libf/libflexdock-java/libflexdock-java-demo_0.5.1-dfsg1-4_all.deb](http://mirrors.kernel.org/ubuntu/pool/universe/libf/libflexdock-java/libflexdock-java-demo_0.5.1-dfsg1-4_all.deb)**


**libjogl-jni** 
```
wget  http://mirrors.kernel.org/ubuntu/pool/multiverse/libj/libjogl-java/libjogl-jni_1.1.1-2ubuntu1_i386.deb
```

[B]
libjogl-java[/B]
```
wget http://mirrors.kernel.org/ubuntu/pool/multiverse/libj/libjogl-java/libjogl-java_1.1.1-2ubuntu1_all.deb  
```


**libjrosetta-java**
```
wget  http://mirrors.kernel.org/ubuntu/pool/universe/libj/libjrosetta-java/libjrosetta-java_1.0.1+gpl-1_all.deb
```


**libmatio0**
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmatio/libmatio0_1.3.3-2_i386.deb
```

**libmatio-dev**
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/libm/libmatio/libmatio-dev_1.3.3-2_i386.deb
```

**libflexdock-java**
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/libf/libflexdock-java/libflexdock-java_0.5.1-dfsg1-4_all.deb
```
 
**libskinlf-java**
```
wget http://mirrors.kernel.org/ubuntu/pool/universe/libs/libskinlf-java/libskinlf-java_6.7-3_all.deb
```

once every last one of the dependency as been downloaded
we then install all of them with one command
```

sudo dpkg -i *.deb
```

once done . we have installed all the dependencies needed by the application.

NOTE: I didnt build this on a fresh ubuntu so they maybe some needed which didnt show up because there were already installed on my computer. so to be save make sure you install build-essential 
```
 sudo apt-get install build-essential 
```

now we start the build.

```
cd ..
```

extract the scilab

```
tar -xzvf scilab-5.0.3-src.tar.gz 
```

enter the directory

```
cd scilab-5.0.3
```

then run configure

```
./configure
```

it would take a while. and if all went well it would return no errors meaning all the dependencies needed for compiling the package is installed. now we run make

```
make
```

this would take a very very long time.. if you have anything else to do .. this is the right time.
i ran this on a pentium dual core 1.8ghz 2gb ram and it took almost 1 hour. 

but once its done 

```
sudo make install
```

it would also take some time to complete .. but once its done without errors that means that scilab 5.0.3 has been installed and can be found in /Application/Education/Scilab

hope some one finds this useful.

PS.. if u run ibex. you dont just 


```
sudo apt-get build-dep scilab
```
```
sudo apt-get install liblaf-plugin-java libjgoodies-looks-java scilab-doc ant sun-java5-jdk  
```

and 

```
sudo apt-get install libflexdock-jni libskinlf-java libflexdock-java libmatio-dev libmatio0 libjrosetta-java jogl-java libjogl-jni libflexdock-java-demo libflexdock-java-doc 
```

before starting the compiling

[COLOR="Black"][B]
For those using Intrepid good news is that u dont have to go thru all the process i went thru just[/B][/COLOR]
In **/etc/apt/sources**, add the line:

    ```
deb http://www.scilab.org/team/sylvestre.ledru/repository/ubuntu/ intrepid main
``` 

Then, the classical commands:

    ```
aptitude update
```
    ```
aptitude install scilab
```

---

### Post by cpgos on 2008-11-22
bigbrovar,
I have followed your installation instructions but have also had some difficulties that I would appreciate help with.

The Scilab gz file was downloaded and saved in $HOME, however on executing sudo apt-get build-dep scilab, a message was displayed saying that a source package for Scilab could not be found; also the following sudo apt-get in your instructions indicated that scilab-doc could not be found.

Next the ten dependencies that you list were downloaded to the directory "dependencies" and on executing the command to install them the output with various errors shown in the attached file was generated. The installation of the dependencies was repeated several times as a message was displayed saying that Fortran 77 and C++ compilers were needed, these were eventually located and installed.

Is the main problem associated with installing the dependencies? I would appreciate any comments that you may have on how to overcome the errors shown in the attached file.

Best regards,
cpgos

---

### Post by bigbrovar on 2008-11-22
hmm looks to me that u may not have all your repositories enabled ... u have to enable all your ubuntu repositories .. because matlab is naturally in the ubuntu repos. but an older version.  make sure that u have all your repos enabled esp the universe repo

---

### Post by cpgos on 2008-11-29
Thank you for your response and my apologies for not responding before now.

I have followed your suggestion but am still having a problem locating the correct version of a package required for libmatio0, the package being libc6 (>= 2.7). As you can see from the attached file, libc.jpg, the installed version is 2.6.1 but version 2.7 or greater is required. Also, it does not seem to be possible to opt for this version via Package/Force Version.

As libmatio0 seems to be involved in compatibility with Matlab I would like to have this facility available.

In addition, the other attached file, dependencies.txt, shows the messages in relation to the above problem. Finally, the package zlib1g-dev has been located and installed.

Any suggestions that you may have would be appreciated.

Best regards,
cpgos

---

### Post by cpgos on 2008-12-05
It seems to me that libc version 2.7 is not available for ubuntu 7.10, which in turn implies that scilab 5.0.3 cannot be used due to dependency problems.

Could somebody please confirm this?

Best regards,
cpgos

---

