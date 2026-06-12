---
title: "COmpiz installation"
date: 2007-11-06
forum: Desktop Effects &amp; Customization
---

### Post by saggylj on 2007-11-06
Hello,

I am a new to ubuntu, infact to the linux community and i guess it will need lot of patience of anyone willing to help as i am absolute blank about configuration etc. i have installed ubuntu 6.06 got myself familiarised and now managed to install Gutsy successfully.

I am trying to make compiz work on my gutsy Desktop which is a DEll optilex GX280 with onboard Intel graphic card 910GL, but when i go to Appearance > visual effect and click on extra i get "desktop effects cannot be enabled" error.

When i type 'compiz' in the terminal i get 'XGL: not present error.
 sudo apt-get install xserver-xgl 
gives me xserver not present error. but in synaptic package manager i can find xserver to be installed.

Can anyone help me get this working. Also i would appreciate if you can direct me to some documentation of some sort to start learning 'editing conigurations and installing drivers etc on ubuntu/linux. as i said i will need milk as i to young to to digest solid stuff.

All help will be much appreciated.

Thanks you 

saggy

---

### Post by Forlong on 2007-11-07
First of all: you do not need Xgl with an intel chip.
Please post the whole output of ```
compiz
``` in a terminal.

---

### Post by teamer on 2008-02-23
Guys i don't know if i have compiz or not . if it's working or not ... after hours of searching Mr.Google and writing some text to the terminal i got this

```
teamer@TeAmErs-Net:~$ sudo apt-get install compiz
[sudo] password for teamer:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
teamer@TeAmErs-Net:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0322 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1024x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (video) - Warn: No 8 bit GLX pixmap format, disabling YV12 image format

```

Any suggestions ???

---

### Post by NightwishFan on 2008-02-23
Please tell me what video card you have and if restricted drivers are enabled. Compiz is installed by default in gutsy, you only need the compiz config settings manager and a compatible graphics card. (as far as i know)

---

