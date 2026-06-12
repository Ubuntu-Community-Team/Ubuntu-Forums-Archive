---
title: "where is my title bar?"
date: 2008-03-20
forum: Desktop Effects &amp; Customization
---

### Post by amazingjxq on 2008-03-20
After I installed compiz by apt-get install compiz, i lost my title bar when I use it.
In the terminal,when I entered compiz,it shows this:

~$ compiz
Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0167 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1280x768) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
/usr/bin/compiz.real (core) - Error: Couldn't load plugin 'ccp'

what's this?

---

### Post by rudyfella on 2008-03-20
you need to install xserver-xgl from Synaptic package manager or use 'sudo apt-get install xserver-xgl'. I have noticed that sometimes Ubuntu Gutsy installation does not install this automatically., You will have to logout & login for changes to take effect.

---

### Post by nisarg on 2008-03-22
OK I am facing this issue as well and it means I cannot enable visual effects. Everytime I try - my windows loose their title bars.
I think it all started when I tried emerald theme manager. I installed it and I imported some kind of glass theme. I think I did play around with my resolution trying to increase it but never really succeeded. 
Now I cannot enable visual effects - I have to have it on NONE.
I have tried installing xserver-xgl - but that hasnt helped. Infact its made it worst - now things like scrolling and opening programs seems choppy and sluggish. I am going to try to remove it. 
Any help appreciated. Thanks. 

> **rudyfella said:**
> you need to install xserver-xgl from Synaptic package manager or use 'sudo apt-get install xserver-xgl'. I have noticed that sometimes Ubuntu Gutsy installation does not install this automatically., You will have to logout & login for changes to take effect.

---

