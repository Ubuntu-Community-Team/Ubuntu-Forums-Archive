---
title: "Can not install GRASS GIS"
date: 2007-02-25
forum: Education &amp; Science
---

### Post by edwardthehead on 2007-02-25
I have been trying to install the GRASS GIS for about two weeks now and can not get anywhere with it.  I have tried to install it a number of different ways and times and I keep getting the same problems.  

I have Unbuntu 6.0.6 that runs fine, don't have any problems.  I have no internet access from Ubuntu and have no interest in getting it which seems to be part of the problem as the only way I can find to install GRASS is via a makegrass.sh that gets everything from the net.  

I have a Gateway AMD Turion64 laptop that has Ubuntu on it.  I have tried to get all the needed *.deb files, but the majority of them will not install because they say they need lib6 installed, which I have.  I tried to install the grass_6.0.0-1_i386.deb, but that tells me I need a fftw2 file.  The fftw6 file says I need a fftw-dev.  The fftw-dev says I need fftw6.  So how do I install one without the other if they need each other? 

I've had this same problem with a few other .deb files saying they need something else only to come back to needing the original files.   I'm now totally confused, frustrated and ready to ditch the entire thing.  I'm sure someone has gotten grass to work, but I sure can't seem to.  

I have actually gotten to the point in the installation and running of GRASS where it asks me to pick my mapsets, but then kicks me out, but that's using the newest version of GRASS that's a generic version and not for Ubuntu.  

Hopefully someone can give me a tip as to where I can find any needed files or what I'm doing wrong.  This is the only thing that wish to do using Unbuntu, as it's a personal learning.  I am willing to switch to another form of Linux, but heard good things about Unbuntu.

---

### Post by timmie on 2007-02-26
I installed GRASS while being connected to the net without any problems.

You can try to run ```
apt-get build-dep grass
``` to see which packeages you need to install before installing Grass

But the Debian packages are a little bit outdated. Therefore it would be better to install all dependencies via apt-get and then unstall GRASS 6**.2.X** manually.

Hope that helps a bit...

---

### Post by edwardthehead on 2007-02-26
> **timmie said:**
> I installed GRASS while being connected to the net without any problems.


Except I'm **not** connected to the net with this computer at all, nor am I going to try and set up an internet connection for this computer.  Basically I want to find the proper files, put them on a USB drive to transfer them to my computer and be done with it.  This is turning out to be much more difficult then it needs to be.

---

### Post by tristan@Ubuntu on 2007-02-27
Well, I don't have the answer if you are not connected to the net.

What I did:
I installed the old (6.0.2) grass version using apt-get, and let apt-get resolve the dependencies. Then, I compiled the version 6.2.1 and 6.3 using the shell scipt that comes with the source, and it works out-of-the-box. 6.3 crashes sometime so I usually use 6.2.1.

-Tristan

---

### Post by timmie on 2007-03-06
> **edwardthehead said:**
> Except I'm **not** connected to the net with this computer at all, nor am I going to try and set up an internet connection for this computer.  Basically I want to find the proper files, put them on a USB drive to transfer them to my computer and be done with it.  This is turning out to be much more difficult then it needs to be.

Well, at some point you will either need to download the files via an internet connection or order a GRASS-CD somewhere.

As far as I know apt-get there's 2 options for you:
on the machine where you have access to the net you can just download with apt-get (not install). THese downloaded packages can be put on the USB and installed by hand.

get all needed packages
sudo apt-get -qq --print-uris install PAKETENAME | awk '{print $1}' | tr -d "'" > wget.list
download packages
wget -i wget.list

Or build your own repository on the USB.
Look at this thread:
[http://ubuntuforums.org/showthread.php?t=7455](http://ubuntuforums.org/showthread.php?t=7455) (Note: I found this via google...)

Last, just install everything by hand since GRASS does list all requirements for its use.

---

