---
title: "Terminal Command"
date: 2010-06-13
forum: Desktop Environments
---

### Post by TheNewbieGeek on 2010-06-13
Hello I need to correct the syntax in the commands for this line:

apt-get install xserver-xorg-video-fbdev xfce4 xfonts-base xinit

Apparently fbdev and xcef are 2 different packages and I don't know the correct syntax to correct this line. thanks

---

### Post by gingivere0 on 2010-06-13
What you have got appears to be perfectly fine, although you're going to need to put sudo in front of it in order to be able to run it if you aren't the root user. This is the exact code:
```
 sudo apt-get install xserver-xorg-video-fbdev xfce4 xfonts-base xinit 
```

---

### Post by golanbatrac on 2010-06-13
Agree with gingivere0. I think you've got it right to begin with (just prepend with sudo):

```
sudo apt-get install xserver-xorg-video-fbdev xfce4 xfonts-base xinit
```That will install the following four programs (and all of their dependencies):
xserver-xorg-video-fbdev
xfce4
xfonts-base
xinit

---

### Post by TheNewbieGeek on 2010-06-13
This is strange I tried the code and it doesn't install linux on my netbook. I tried seeing if I can connect to the internet with the command dhclient and dhclient eth0 but I can't tell. What should the output say if you're connected?

---

### Post by nothingspecial on 2010-06-13
```
sudo ifconfig eth0 up
sudo dhclient
```

Then try again.

---

