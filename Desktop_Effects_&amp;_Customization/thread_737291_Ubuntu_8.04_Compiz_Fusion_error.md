---
title: "Ubuntu 8.04 Compiz Fusion error"
date: 2008-03-27
forum: Desktop Effects &amp; Customization
---

### Post by L33t Masta on 2008-03-27
I'm a new linux user and I've tried to run through the community documentation, but when I run compiz --replace I get this:

l33t@l33t-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0407 (rev a1) (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1440x900) to maximum 3D texture size (8192): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Warn: Unable to parse XML metadata from file "ccp.xml"
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format
GConf backend: There is an unsupported value at path /apps/compiz/plugins/scale/allscreens/options/initiate_edge. Settings from this path won't be read. Try to remove that value so that operation can continue properly.


I'm using a Dell XPS M1530
2GB RAM
256MMB nVidia 8600M GT
2.2 GHz dual core CPU
1440 x 900 resolution screen

---

### Post by adityakavoor on 2008-03-27
you need to install Nvidia drivers

try [envy]("http://www.albertomilone.com/nvidia_scripts1.html")

---

### Post by kodoku on 2008-03-27
would the driver in the repositories work as well?

> sudo apt-get install nvidia-glx-new

---

### Post by L33t Masta on 2008-03-27
> **adityakavoor said:**
> you need to install Nvidia drivers

try [envy]("http://www.albertomilone.com/nvidia_scripts1.html")

I thought that's what restricted drivers were.

l33t@l33t-laptop:~$ sudo apt-get install nvidia-glx-new
[sudo] password for l33t: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
nvidia-glx-new is already the newest version.
The following packages were automatically installed and are no longer required:
  libqt3-mt
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

---

### Post by L33t Masta on 2008-03-27
I'm trying now but it's giving the same error.

---

### Post by dbp876 on 2008-04-05
Yes I am getting the same error, any info would help!
Thanks

---

### Post by dbp876 on 2008-04-05
[http://ubuntuforums.org/showthread.php?t=643485&highlight=%2Fapps%2Fcompiz%2Fplugins%2Fscale%2Fallscreens%2Foptions%2Finitiate_edge](http://ubuntuforums.org/showthread.php?t=643485&highlight=%2Fapps%2Fcompiz%2Fplugins%2Fscale%2Fallscreens%2Foptions%2Finitiate_edge)



Try this link. It worked for me

---

