---
title: "How to uninstall and reinstall NVIDIA driver"
date: 2009-01-24
forum: General Help
---

### Post by lcolson on 2009-01-24
I'm looking for some help on how to uninstall and reinstall the latest NVIDIA driver.  

Ever since I upgraded to 8.10, I haven't been able to get the visual effects to work.  With the previous releases it would work fine.  I have a 9600GT, and I downloaded the latest NVIDIA driver 

NVIDIA-Linux-x86-180.22-pkg1.run

that is now sitting on my desktop.  I have tried installing and uninstalling numerous times (and previous versions of the driver) over the past few months (apparently the installs weren't successful), so at this point I'm not sure what is installed or not.  I've tried several other peoples walk throughs i.e. 

[http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+9600gt](http://ubuntuforums.org/showthread.php?t=990978&highlight=nvidia+9600gt)

but apparently I never got it just right.  

I would really appreciate the help.  Thanks.

---

### Post by 2hot6ft2 on 2009-01-24
You could install envyng and use it to do it. with ```
sudo apt-get install envyng
```in a terminal.
Applications>Accessories>Terminal
then it will be in
Applications>System Tools>EnvyNG

The recommended way to install the graphics driver is of course thru.
System>Administration>Hardware Drivers

---

### Post by lcolson on 2009-01-24
Thanks.  

I had no idea what the EnvyNG thing in my system tools was (I had it already).  But I uninstalled my driver and did a forced install of one after it failed to recognize my card and presto.  

Visual effects are working again now.  :D

---

