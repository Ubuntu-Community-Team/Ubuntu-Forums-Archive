---
title: "NWN/Graphics Question from Linux Noob"
date: 2006-01-04
forum: Gaming &amp; Leisure
---

### Post by Raymosexual on 2006-01-04
Okay so I have a few questions.  I installed NWN according to the instructions on the BioWare website.  I also installed all the SDL libraries after i saw [this thread]("http://www.ubuntuforums.org/showthread.php?t=92938&highlight=neverwinter+nights").  However, when I try to run ./nwn i get this error:

Failed to initialize graphics.
Fatal Signal: Segmentation Fault (SDL Parachute Deployed)

I tried to install the newest nVidia drivers (I have an fx5200 256MB) but I don't know how to end x server state so I can install them. Or perhaps something else is wrong. Any help would be much appreciated.

---

### Post by Omnios on 2006-01-04
try sudo ./nwn

---

### Post by Raymosexual on 2006-01-04
Didn't work

---

### Post by Omnios on 2006-01-04
sounds like something whent wrong with the install, did you follow all the proper steps? I have reinstalled nwn a few times because of bad installs. Check your version against the instructions. If you have half decent hardware it will run fine with the standard install. I have a p4 1.6ghz with a GeForce MX4000 and it runs amazing.

 Edit: you may be able to solve the problem though so id keep asking

---

### Post by Raymosexual on 2006-01-04
Reinstalled and got the same error message.
I havn't installed any nVidia driver since I installed Breezy, could that be a problem?

---

### Post by Omnios on 2006-01-04
did you install nvidia-glx that is the one you needif you are using the graphics driver from the install nv driver it does not support 3d

 In terminal:

 sudo apt-get install nvidia-glx
 sudo nvidia-glx-config enable

sudo nvidia-glx-config enable: make shure this part works because it sets up Xserver to use the nividia driver

---

### Post by Raymosexual on 2006-01-04
Well, I didn't have nvidia-glx installed, so I did a sudo apt-get install and that worked, but alas I'm still getting the same error.

---

### Post by Omnios on 2006-01-04
This is from the Unofficial Ubuntu Guide for installing the drivers.

[http://ubuntuguide.org/#installnvidiadriver]("http://ubuntuguide.org/#installnvidiadriver")

 You will also have to install extra repositoies by uncommenting them (removing # in the sources list)

[http://ubuntuguide.org/#extrarepositories]("http://ubuntuguide.org/#extrarepositories")


sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list



 think you can do this grom synaptic also which may be easier.

---

### Post by Raymosexual on 2006-01-04
Ok so that works fine now and when i tried ./nwn i didn't get the graphics failure, but i still got the segmentation fault. So i reinstalled and still nothing. Screen goes black for a minute and then goes back to terminal showing segmentation error.

---

### Post by Omnios on 2006-01-04
Try it with sudo again. I remember I had to use sudo to get it to run properly.

 Also check out this NWN thread about players.

[http://ubuntuforums.org/showthread.php?t=111284]("http://ubuntuforums.org/showthread.php?t=111284")

 ALso if you have a fram rate problem where the mouse does not work properly there is a fix for that on the Bioware forum but not a problem with a Geforce MX4000

---

### Post by kaamos on 2006-01-05
Have you made sure all the files in nwn have correct permissions? This may cause segmentation faults, and personally I just did
```
chmod +rx Folder_Of_Nwn -R
```

---

