---
title: "How To Change Screen Resolution?(Fedora 10)"
date: 2009-02-22
forum: General Help
---

### Post by zohaib44 on 2009-02-22
Hi everyone

today I installed fedora 10 when i go to system > preferences > hardware > screen resolution it shows only 800x600 and 640x480, I cannot change my screen resolution to 1024x768.

is there any other way to change screen resolution?

thanks

---

### Post by evilGUI on 2009-02-22
Yeah there is you have to edit xorg.conf with:
```
su
```
```
cp /etc/X11/xorg.conf xorg.conf.backup
```
```
gedit /etc/X11/xorg.conf
```

And add Modes "resolution goes here"

heres what mine looks like yours will differ:
```
Section "Screen"

Identifier "Default Screen"

Device "Generic Video Card"

Monitor "Generic Monitor"

DefaultDepth 32

SubSection "Display"

Modes "1280x768"

EndSubSection

EndSection
```

save all your work and Hit ctrl alt + backspace after your done.

If for some reason you can't start x, restart boot into single user mode by adding 1 to the end of your grub boot options and type ```
su
``` ```
cd /etc/X11/
``` ```
rm xorg.conf
``` ```
mv xorg.conf.backup xorg.conf
```

If you have any issues, you can talk with us in #fedora on irc.freenode.net.

---

### Post by sriharsha2410 on 2009-06-21
hi, even i have the same problem. i tried to follow your steps, but i couldnt find any file named 

xorg.conf
in
/etc/X11 
how am i supposed to change my screen resolution. should i install any graphics drivers. if so then where to find them.

---

