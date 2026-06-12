---
title: "missing title bars"
date: 2007-06-22
forum: Desktop Effects &amp; Customization
---

### Post by stuffer007 on 2007-06-22
I am a noob to Ubuntu, but fairly decent with windows. i just finished setting up a dual boot with feisty and XP Media center. My video card is a GeForce 7950GX2 and I have Beryl running im not sure what setting i have changed but i lost the the title bars on all the windows (file, edit....) also i have a wide screen LCD monitor and cannot seem to get the res to work correctly, once i do get the resolution to work the right side looks smeared. but as soon as i log off/restart it goes back to original settings. if anybody could direct me in any direction from hear it would be greatly appreciated.

---

### Post by raul_ on 2007-06-22
[http://www.google.com/search?q=ubuntu+forums+beryl+compiz+no+bars&start=0&start=0&ie=utf-8&oe=utf-8&client=mozilla&rls=org.mozilla:en-US:unofficial]("http://www.google.com/search?q=ubuntu+forums+beryl+compiz+no+bars&start=0&start=0&ie=utf-8&oe=utf-8&client=mozilla&rls=org.mozilla:en-US:unofficial")

;)

How do you get the resolution to work?

---

### Post by stuffer007 on 2007-06-22
I go into the nvidia device settings and change it to 1280x768, but it smears the the right side of the screen. if you take the 1024x768 (default) the extra add on to 1280x768 smears. but when i log off/restart it does not stay in the new settings, it reverts to the default.

---

### Post by raul_ on 2007-06-22
Try this then:

sudo cp /etc/X11/xorg.conf /etx/X11/xorg.conf_backup

sudo gedit /etc/x11/xorg.conf

scroll down until you reach the resolutions section, and then change the default one to your custom resolution

Did you solve the bars problem already?

EDIT: i forgot. If that breaks your X, i.e, if you get thrown at a terminal just do 

sudo cp /etx/X11/xorg.conf_backup /etc/X11/xorg.conf

---

### Post by stuffer007 on 2007-06-23
Yes and no, if i disable beryl the title bars come back. so ive narrowed it down to beryl (back to square 1) now i just have to find what setting needs to be tweaked

---

### Post by Minus_Fireal on 2007-06-23
Try typing this in a console : sudo nvidia-xconfig -add-argb-glx-visuals -composite

---

