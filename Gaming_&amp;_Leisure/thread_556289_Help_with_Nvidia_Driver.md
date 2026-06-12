---
title: "Help with Nvidia Driver"
date: 2007-09-21
forum: Gaming &amp; Leisure
---

### Post by jonaaathan on 2007-09-21
Hey everyone, I'm pretty new to linux so I could use some help.  I finally got my Geforce 7300GT installed by using Envy and I realized that the NVIDIA driver isn't being used.  I did ```
cat /proc/driver/nvidia/agp/status
``` and it gave me this: 

Status:          Enabled
Driver:          AGPGART
AGP Rate:        8x
Fast Writes:     Disabled
SBA:             Enabled

What am I to do in order to make the driver show NVidia?

---

### Post by Mr. T on 2007-09-21
There's a much easier way (provided you're running Feisty).

Goto System -> Administration -> Restricted Drivers Manger.

There should be a checkbox you can enable, it will download and install/setup the driver for you. It's pretty easy. I would recommend uninstalling anything Envy did and try this instead.

---

### Post by jonaaathan on 2007-09-21
I uninstalled all the Nvidia drivers by using Envy and tried installing the drivers through the Restricted Drivers Manager.  Itt asked me to restart and I did. However, my Xorg.conf is messed up. Am I supposed to edit something in my Xorg.conf before I restart?

---

### Post by Sockerdrickan on 2007-09-21
Use the old one (should be a backup one)

---

### Post by jonaaathan on 2007-09-21
So I reseted my xorg.conf by doing ```
sudo dpkg-reconfigure xserver-xorg
```.  I set everything to the default settings.  So now, when I try to view the nvidia settings, all the options are no longer there. besides enable tooltips, display status bar, etc.  Do I need to get anything else like the nvidia kernel or anything? If so how?

---

### Post by jonaaathan on 2007-09-21
Okay, I got the driver installed, however now when i go to  "cat /proc/driver/nvidia/agp/status
" , it shows that the status is disabled. How do I enable it?


--- Just curious though, is there any way to prevent AGPGART from loading?

---

