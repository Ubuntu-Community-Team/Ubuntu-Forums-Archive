---
title: "How do I change my PC's hostname?"
date: 2005-08-20
forum: Desktop Environments
---

### Post by arcanistherogue on 2005-08-20
So.  I wanted to change it from PC to kubuntu, and I edited the /etc/hostname file.  Then, someone on the kubuntu IRC said to do "sudo hostname <newname>".  I did this, then when I closed the Konsole I couldn't launch anymore applications.  The icon near the cursor kept bouncing, but then it just stopped after a while.

I did alt-ctrl-F1 and edited /etc/hosts also, but this didn't work.  I changed them all back, but it still won't work. 

When I reboot It starts the command line and not KDE.

How do I change this back?

---

### Post by nad on 2005-08-20
Several daemons and services depend on the hostname of the system. Once changed, they need to be restarted.

If you can log in to your system, edit the /etc/hostname file (to whatever name you wish), then run: shutdown -r now , to cleanly reboot your system.

If you can't log in, boot into single mode or use a rescue cd to edit the hostname file.

---

### Post by arcanistherogue on 2005-08-21
I can login.  I changed /etc/hostname, /etc/hosts, and did "sudo hostname <newname>".  Then I did "sudo shutdown -r now".  

It didn't work, I still log in on the command line.  I tried "startx", and it says it can't find the nvidia kernel.  I'm assuming this is because the nvidia kernel needs the hostname.  

What I plan to do is change the driver to the default one (before i edited xorg.conf it was "nv", i changed it to "nvidia" and it worked.) which i changed to nvidia because it didn't load and i couldnt play games.

If i changed it back, apt-get remove nvidia-glx, apt-get install nvidia-glx, will that work?  I say this because I changed my computers name from ubuntu to kubuntu earlier before I installed the nvidia glx drivers and nothing bad happened.

---

### Post by nad on 2005-08-21
(shrugs) Something got borked. I would say that gdm is having problems, but you've got that nvidia message.

I'm also not sure if startx will work. You need gdm: /etc/init.d/gdm restart .

---

### Post by arcanistherogue on 2005-08-21
I'll try that out, but I am using KDE.

---

### Post by nad on 2005-08-21
Just replace gdm with kdm .

---

### Post by Velox Letum on 2005-08-21
If this doesn't work, open up /etc/X11/xorg.conf and find the Section "Device" and change the driver to visa, then reinstall your nVidia drivers.

---

### Post by kooldino on 2007-11-20
You mean VESA?

---

