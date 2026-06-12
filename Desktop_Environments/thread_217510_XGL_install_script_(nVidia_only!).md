---
title: "XGL install script (nVidia only!)"
date: 2006-07-17
forum: Desktop Environments
---

### Post by PryGuy on 2006-07-17
Good day everybody!
I have [read the article about the XGL installation]("http://ubuntuforums.org/showthread.php?t=131267") and composed a little script that makes it easy to install XGL 'cause I'm very lazy to do it every time on other machines. :) Yet, this script assumes that you have nVidia video card and it's drivers installed and configured properly.

**And please remember, the script is buggy probably and use it on your own rusk and only if you understand what it does.**

So, here we go:
First, create a folder. I called it 'xgl'. Create a new file called 'thefuture' there and paste this text in it:```
#!/bin/bash
gnome-window-decorator &  compiz --replace gconf decoration wobbly fade minimize cube rotate zoom scale move resize place switcher &
```Then, create a new file called 'install.sh' and paste the following code there:```
#sudo dpkg -i libglitz1_0.5.3-0ubuntu2_i386.deb
#sudo dpkg -i libglitz-glx1_0.5.3-0ubuntu2_i386.deb
#sudo dpkg -i libxcomposite1_1%3a0.2.2.2-0ubuntu2_i386.deb
#sudo dpkg -i compiz_0.0.2-4ubuntu2_i386.deb
#sudo dpkg -i compiz-gnome_0.0.2-4ubuntu2_i386.deb
#sudo dpkg -i xserver-xgl_7.0.0-0ubuntu4_i386.deb
sudo apt-get install compiz xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 compiz-gnome

sudo cp -f thefuture /usr/bin/thefuture
sudo chmod 755 /usr/bin/thefuture

#sudo sed -i '/"dri"/a\		Load "glx"' /etc/X11/xorg.conf
sudo sed -i '/"PCI:1:0:0"/a\	Option		"RenderAccel"	"true"' /etc/X11/xorg.conf

sudo sed -i '$a\0=Xgl' /etc/gdm/gdm.conf-custom
sudo sed -i '$a\[server-Xgl]' /etc/gdm/gdm.conf-custom
sudo sed -i '$a\name=Xgl server' /etc/gdm/gdm.conf-custom
sudo sed -i '$a\command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo ' /etc/gdm/gdm.conf-custom
sudo sed -i '$a\flexible=true' /etc/gdm/gdm.conf-custom

```I have commented the lines that assume that you have the files downloaded but you can enable them if you wish.

I'm waiting for your thoughts/script corrections. Thanks in advance!:D

---

### Post by asplode on 2006-07-17
I like the thought, perhaps you could include some direct wget commands to make it extra easy, and create its own directory.

---

### Post by PryGuy on 2006-07-18
Yeah, right! But have you tried the script?

---

### Post by asplode on 2006-07-18
no, I haven't tried it because I have gone through poofyhairguy's guide several times from fresh installs + drivers, and 'thefuture' only kills all my gnome panels and window chrome, so I am personally holding off until xgl/compiz becomes stable enough to... yknow... work.

---

### Post by PryGuy on 2006-07-18
do you have nVidia card?

---

### Post by asplode on 2006-07-18
> **PryGuy said:**
> do you have nVidia card?

indeed I do.

---

### Post by PryGuy on 2006-07-18
I do not see why do you have problems then.

---

### Post by evilghost on 2006-07-21
I too am waiting before implementing XGL so that Nvidia will support the GLX_EXT_texture_from_pixmap function without the need to use Mesa, this should be in the 1.0.9xxx drivers.

---

### Post by ashmew2 on 2007-02-16
Hey i know this is a very old thread but i really want to know some things..


> I have commented the lines that assume that you have the files downloaded but you can enable them if you wish.
#sudo dpkg -i libglitz1_0.5.3-0ubuntu2_i386.deb
#sudo dpkg -i libglitz-glx1_0.5.3-0ubuntu2_i386.deb
#sudo dpkg -i libxcomposite1_1%3a0.2.2.2-0ubuntu2_i386.deb
#sudo dpkg -i compiz_0.0.2-4ubuntu2_i386.deb
#sudo dpkg -i compiz-gnome_0.0.2-4ubuntu2_i386.deb
#sudo dpkg -i xserver-xgl_7.0.0-0ubuntu4_i386.deb


as far as i know even if i unhash those lines , they wont "DOWNLOAD" the files ....dpkg is an installer program , it needs the .deb files for insatlling which i dont have on my system. 

And secondly , what ami supposed to do with "thefuture" file and the install.sh (IM A COMPLETE NEWBIE!!!!!).

Please correct me if im wrong and do post ASAP
Thanks

---

