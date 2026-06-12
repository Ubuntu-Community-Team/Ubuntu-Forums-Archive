---
title: "No Desktop Icon"
date: 2008-03-17
forum: Desktop Effects &amp; Customization
---

### Post by hormati on 2008-03-17
Hi,
I am running ubuntu gutsy on my desktop with an nvidia card. I already have the latest version of the nvidia driver. After enabling compiz, all my desktop icons disappeared! :confused: It's really strange. Any help will be highly appreciated!! 

Amir

P.S: I don't know if it matters, but I have a dual monitor setup. I am also running screenlets.

---

### Post by Ub1476 on 2008-03-17
Have you tried to open Desktop with Nautilus (filemanager)? Maybe they are hidden for some reason. Open Desktop with your filemanager (from home folder) and press ctrl+h to see hidden files. If you are missing Computer, Trash, Network etc launchers on your desktop, those can be enabled in 

```
gconf #launcher name might be "gconfeditor"
```

then, apps>nautilus>desktop.

---

### Post by hormati on 2008-03-17
That did not help. I have files and shortcuts other than Computer, Network, Trash, etc. in the Desktop folder and they are not hidden. 
I just discovered something really really strange. I can't see the icons, but when I double click on the desktop background on the exact same location where the icons used to be, the related programs run. It's like the icons are there but are invisible. 

I checked the "show desktop" option in gconf-editor, that's already enabled. I am totally confused!

Thanks,
Amir

---

### Post by hormati on 2008-03-18
bump!

---

### Post by Kabezon on 2008-03-18
do ALT+F2 and type "nautilus" see if something happens.

---

### Post by hormati on 2008-03-18
Running nautilus opens a new file browser window, but it does not change anything about the desktop icons. Still, I can't see any of the desktop icons :confused:

Amir

---

### Post by Therion on 2008-03-18
See the bottom of [this page](http://www.psychocats.net/ubuntu/nonautilusplease) about restoring Nautilus as your default file manager.

---

### Post by hormati on 2008-03-19
That didn't help. :(
Amir

---

### Post by hormati on 2008-03-19
The funny thing is that, this only happens when I enable dual screen mode in the nvidia-settings tool. If I use only one screen, I can see the icons and everything is fine!

Is there anything special in the xorg.conf related to the icons?
Thanks
Amir

---

### Post by hormati on 2008-03-20
bump!

---

