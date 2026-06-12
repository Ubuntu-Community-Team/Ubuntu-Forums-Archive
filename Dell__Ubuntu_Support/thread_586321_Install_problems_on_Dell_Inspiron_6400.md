---
title: "Install problems on Dell Inspiron 6400"
date: 2007-10-22
forum: Dell  Ubuntu Support
---

### Post by MeteoraLP on 2007-10-22
Hey guys, 

having troubles installing Linux on my dell laptop. I boot from CD and get to the splash screen. I select start or install ubuntu and then i get a loading bar, then the screen goes black with cursor at the top corner. Then my screen starts flashing weird colors. After a while i get a message saying something like the display server has failed 6 times in 30 seconds.

Not sure exactly what is going on. First time installing linux!

my specs are:

Dell Inspiron 6400
Intel C2D 
ATI x1400 
2gb ram
Vista on another partition

Thanks!

---

### Post by kmpa on 2007-10-22
Hi guys,
I have the same problem too and my specs are the same as the above, and I hope any one to help me in it please.

Note: this problem happened with me when I tried to install the 64bit version of ubuntu 7.04 but when I tried to install the 32bit version it was installed successfully.

Please help.

---

### Post by staticsage on 2007-10-22
I've had problems installing before and it has almost always been the install media. 

When you boot off the CD, select the  "Check CD for defects" option.

If you come up with errors, I recommend burning the CD at the lowest possible speed.

---

### Post by MeteoraLP on 2007-10-22
Tried that already, came up with no errors. I guess i could try to reburn the install disk.

---

### Post by leong on 2007-10-22
i just had it before when i install 7.10 in my laptop, below is what i was done:

1) boot from cd
2)use "boot option" change to *single* mode ( delete the last word change it to "single" 
3)will start in text mode  as root , use *dpkg-reconfigure xserve-xorg* 
configure video to* vesa *
4)*exit * will boot in gui screen .

try it ! it is in 7.10

---

### Post by djRob on 2007-10-23
ATI doesn't give a crap about Linux so you have problems. 
I have the same laptop and installed Ubuntu 7.10 on it. You have to use alternate CD and chose text mode installation. Before installation disable Wi-Fi (I don't use Wi-Fi). After installation you have to login into text console and install ATI proprietary driver manually, here is how
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

