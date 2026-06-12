---
title: "Screen resolution"
date: 2010-09-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by jlfrank21 on 2010-09-29
I just installed Ubuntu last week and plugged my laptop into my 47" tv.  Does ubuntu only support these resolutions? I'd really like it at 1600x1200, similar to when I'm in Windows.

1024 x 768
800 x 600
640 x 480

---

### Post by Dex73 on 2010-09-29
I'm not sure but I can tell you that mine is 1280x800 (16:10), so it should be possible to make it at least a little better. Just to give you an idea of my set up, I'm using a Gateway laptop. Here are my system details in this pic.

---

### Post by jlfrank21 on 2010-09-29
Well, I figured out that it was mirroring laptop image to my tv which was resulting in the limited resolutions. I've now go it displaying on my tv only and disabled laptop display. I need to figure out how to get the computer to stay on when I close the laptop and how to get the Green square in the top left of my display to come off. Right now it has the name of my tv, and I cannot move it.

---

### Post by Dex73 on 2010-10-04
Go to System/Preferences/Power Management to change what happens when the lid is shut both on and off ac power.

---

### Post by Thomas_Bates on 2010-10-04
Please post your graphics card, such as Nvidia GeForce 7100 (example). Also post your xorg.config file.

gksudo gedit /etc/X11/xorg.config

Edit:

Also, look for a tag on your TV with the television's model number. Alternatively, if you've still got the manual, type in the model number into Google and search for Native Resolution (it may/may not be in the manual, mine wasn't).

---

