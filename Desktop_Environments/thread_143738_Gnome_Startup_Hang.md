---
title: "Gnome Startup Hang"
date: 2006-03-13
forum: Desktop Environments
---

### Post by Fizzyboy on 2006-03-13
After installing a server installation of Breezy on my K6-2 333MHz/ATi Rage Pro machine.
I apt-get'ed xserver-xorg, x-window-system-core, and gdm.

After running 'start x', X starts up and the ubuntu startup banner comes up loading all the things. When it gets to the third option 'Nautilus' it doesn't get any further. I can still move the cursor but nothing happens.

Thanks.

---

### Post by gord on 2006-03-13
```
sudo apt-get ubuntu-desktop
``` 
should sort you out :)

if you did a server install to get more of a basic system though, i would try doing
```
sudo apt-get install nautilus gnome-panel
```

that should get you the basic stuff you need to get a gui going :)

---

### Post by Fizzyboy on 2006-03-13
Thanks, I will try that.
One more question while I am at it...
What is the keyboard command to escape to the console? So I don't have to reboot the physical machine. ^^;

---

