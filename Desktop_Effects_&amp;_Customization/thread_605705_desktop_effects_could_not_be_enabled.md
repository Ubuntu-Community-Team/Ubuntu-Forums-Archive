---
title: "desktop effects could not be enabled"
date: 2007-11-07
forum: Desktop Effects &amp; Customization
---

### Post by m4cm0 on 2007-11-07
Hi, I have just installed Ubuntu 7.1 onto my Dell inspiron 8200 laptop which has a NVIDIA GeForce2 DDC (generic) Graphics Card. The problem is that every time i try to activate the extra effects on the desktop background visual effects a window pops up saying that "desktop effects could not be enabled". Ive checked my restricted drivers and the NVIDIA accelerator graphics driver has been enabled. I have also installed Compiz Config manager, and rebooted, but no luck. Is it just that my graphics driver unable to process these effects? Does anyone have the same Laptop. Your help would be appreciated.

---

### Post by FuturePilot on 2007-11-07
I have the same laptop. Only it has a Nvidia GeForce2 Go in it. 
Can you post the output of
```
compiz --replace
```
Just put that in a terminal

---

### Post by m4cm0 on 2007-11-07
I've managed to resolve the problem from thefollowing thread.  Thanks
Ubuntu Forums > The Ubuntu Forum Community > Main Support Categories > Ubuntu Dell Support  
 desktop effects could not be enabled  

thanks:)

---

### Post by mr_pro_2020 on 2008-02-04
Plz  FuturePilot 

i have tried What U say

> compiz --replace

And It Was That

> mrpro@mrpro-laptop:~$ compiz --replace
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0176 (rev a3) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x800) to maximum 3D texture size (2048): Passed.
Checking for nVidia: present. 
Less than 65536kb of memory and nVidiaaborting and using fallback: /usr/bin/metacity 


My card is GeoForce 420  with 32Mb
How can i make it work??!!

---

### Post by mr_pro_2020 on 2008-02-04
fIRST For Ur Nvidia Card   seee that

[http://ubuntuforums.org/showthread.php?t=630898](http://ubuntuforums.org/showthread.php?t=630898)

and then


I have Found This partcialy Sol 

AT [http://ubuntuforums.org/showthread.php?t=596927](http://ubuntuforums.org/showthread.php?t=596927)

> sudo apt-get install xserver-xgl


> compiz --replace

and restart And See :D

---

### Post by FuturePilot on 2008-02-04
> **mr_pro_2020 said:**
> Plz  FuturePilot 

i have tried What U say



And It Was That



My card is GeoForce 420  with 32Mb
How can i make it work??!!

That might be a problem. The Compiz wrapper in Gutsy has a 64MB VRAM minimum limit on it for Nvidia cards. There is a way around it, but it may cause black windows due to a bug in the Nvidia driver. [B]Do this at your own risk.
[/B][http://ubuntuforums.org/showpost.php?p=3479836&postcount=4]("http://ubuntuforums.org/showpost.php?p=3479836&postcount=4")

---

### Post by mr_pro_2020 on 2008-02-05
Yes Ihave tried that Sol 

But  It not working right as it must

---

### Post by vinutux on 2008-02-06
install "xserver-xgl" and re-login or restart.............try it may be.......a little hope

---

### Post by theproc64 on 2008-02-08
I tried this and many windows and menus were black and none of the windows had toolbars.

---

### Post by vinutux on 2008-02-08
can u explain more? or  attach a screenshot plz

---

