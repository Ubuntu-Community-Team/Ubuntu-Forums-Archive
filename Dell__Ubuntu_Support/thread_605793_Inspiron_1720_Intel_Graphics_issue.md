---
title: "Inspiron 1720 Intel Graphics issue"
date: 2007-11-07
forum: Dell  Ubuntu Support
---

### Post by Soabirw on 2007-11-07
I installed Ubuntu 7.10 on my Inspiron 1720 last night and the display seemed to work just fine.  But then when I took it into work the next day and started it up the display was scrunched.  So I tried setting the resolution back to 1920x1200 and it fails and asked me to reconfigure every time.  I can't seem to get it to go above 800x600 now and I can't figure out why.  This laptop was given to me at work, so I'm not positive on the specs, but Windows claims the graphics card is Mobile Intel 965 Express.  Most of the threads I find are people with nVidia or ATI graphics cards, so I'm not sure if that's correct or not.  The driver that Ubuntu is using is just the Vesa compatible.

Can anybody post a xorg.conf that should work with the Intel graphics on a Inspiron 1720?  Or is there a way to rerun a auto config that will create that original xorg.conf that seemed to work?  I think what ended up confusing it was when I hooked up my external monitor.  Which is something I'd also like to get working, but I'd be happy just to have my laptop display work properly for now.

Any help is greatly appreciated.

---

### Post by Triptol on 2007-11-13
You could try changing the "driver" option in xorg.conf to i810

like

Driver "i810"

---

### Post by jdelaros1 on 2007-11-13
Have you tried running dpkg-reconfigure xserver-xorg?

1. Go to a virtual terminal: Ctrl + Alt + F1
2. Stop GDM: sudo /etc/init.d/gdm stop
3. sudo dpkg-reconfigure xserver-xorg

- select default values in almost all windows
- when selecting a driver, try 'intel' 
- make sure you select the appropriate resolutions

When done, restart GDM with sudo /etc/init.d/gdm start

---

### Post by sciurus on 2007-11-22
[http://ubuntuforums.org/showthread.php?t=617934](http://ubuntuforums.org/showthread.php?t=617934)

---

