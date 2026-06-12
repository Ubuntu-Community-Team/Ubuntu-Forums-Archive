---
title: "Can't init SDL unless running as root?"
date: 2020-06-23
forum: Emulators
---

### Post by Gary Kleppe on 2020-06-23
I finally replaced my nine-year-old Linux computer and am trying to  get the new one set up. After installing Ubuntu  20.04 LTS, I installed both Tile World, which I compiled  from source, and Dosbox which I installed through apt-get. Both of them  require SDL so I had to install this first.

 
The problem: The installed games won't run unless I'm root. If I run  from the start menu, nothing happens. In console, it tells me that it  can't initialize SDL because "No available video device".

 
Interestingly, I *can* run either of these games via sudo. When I do, though, it runs it full screen, not in a window.

 
I'm wondering if some library file needs permissions? Anyway, any  suggestions or other help would be appreciated. Thanks in advance.

     

In case it matters, my graphics card is a NVIDIA Corporation GK208B [GeForce GT 710] using NVIDIA driver metapackage nvidia-driver-440.

---

### Post by deadflowr on 2020-06-24
There should be a conf file in ~/.dosbox.
Check the ownership and perhaps try changing the output setting.
The file gives the options available. Default should be surface, but there should be others like opengl and overlay.

(check the ownership because chances are if run as root the ownership is now root,
so maybe resetting the owner to your user  may help.)

Oh, and...
*Thread moved to **Emulators***

---

### Post by Gary Kleppe on 2020-06-27
Thank you for looking at this. I tried moving the dosbox executable from /root/ (where the installer put it for some reason) to /usr/bin, and made sure that my user has access to both that and the config file as well as ownership of both. Also tried moving the executable into my own home directory. Also tried various other options for output in the config file. Still no dice. When running as myself it says Can't init SDL No available video device. When running as root via sudo, it insists on going full-screen even though that option isn't set in the config file. It also messes up the keyboard mapping, but that's probably a separate issue.

---

### Post by deadflowr on 2020-06-28
> I tried moving the dosbox executable from /root/ (where the installer put it for some reason) to /usr/bin
?
How'd you install it?

---

### Post by Gary Kleppe on 2020-06-29
I believe it was through sudo apt-get.

---

