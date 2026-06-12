---
title: "daisy dock install fails"
date: 2011-03-06
forum: Desktop Environments
---

### Post by pedorro on 2011-03-06
I'm running KDE 4.6 on Maverick using the backports repository.  When I try to install 'plasm-widget-daisy' I get the following error:

```
sean@Oberon:~$ sudo apt-get install plasma-widget-daisy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 plasma-widget-daisy : Depends: libtaskmanager4a (>= 4:4.4.0) but it is not going to be installed
E: Broken packages
```
It looks like it's saying it needs 'libtaskmanager4a' >= 4.4.

Trying to install that leads to the following:
```
sean@Oberon:~$ sudo apt-get -s install libtaskmanager4a
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 libtaskmanager4a : Depends: libkephal4 (= 4:4.5.1-0ubuntu8) but it is not going to be installed
E: Broken packages
```
So why would it have a dependency on something for KDE 4.5?

I'm guessing there's probably something wrong with the way dependencies are configured, but I don't really know much about how apt & dpkg work.

Any ideas?  Thanks.

---

### Post by inobe on 2011-03-06
what it says is what it is, it's broken on kde 4.6

assuming, daisy will eventually be developed to work on kde 4.6 at a later time.

the package manager is preventing system damage.

edit: it may work in natty, not sure [http://www.ubuntuupdates.org/packages/show/288059](http://www.ubuntuupdates.org/packages/show/288059)

the current version for 10.10 is 4.23, notice updated version for natty.

---

### Post by ankspo71 on 2011-03-07
Hi,
I had the same error as you did while trying to install plasma-widget-daisy in KDE 4.6.1 too, but I was able to download the source code for daisy and easily compile it myself.

First I went to the daisy _[homepage]("http://cdlszm.org/pages/download.php")_ and downloaded the source package called plasma-applet-daisy-0.0.4.25.tar.gz. Then I extracted the package on my desktop. 

Dependencies:
The instructions found in the README and INSTALL files said I needed the following dependencies: kdebase-workspace-dev, kdelibs5-dev, gcc, and cmake.

So I installed them in the terminal with this command:
```
sudo apt-get install kdebase-workspace-dev kdelibs5-dev gcc cmake
```

Compilation and Installation:
First I opened my terminal and navigated to the extracted source package on my desktop.
```
cd /home/james/Desktop/plasma-applet-daisy-0.0.4.25/
```

Then I used a few commands to compile and install daisy. Here are the recommended commands found in the INSTALL file:

```
mkdir build
cd build
cmake ../ -DCMAKE_INSTALL_PREFIX=`kde4-config --prefix`
make
sudo make install
kbuildsycoca4

```

Alternately, the following commands might also work:

```
cmake .
make
sudo make install
```

Hope this helps.

---

