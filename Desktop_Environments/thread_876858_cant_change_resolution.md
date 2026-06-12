---
title: "cant change resolution"
date: 2008-08-01
forum: Desktop Environments
---

### Post by Existance0 on 2008-08-01
Built a new computer:
GeForce 8800GTS
AMD Phenome tricore processor

Well logged in for the first time ubuntu downloaded all its updates rebooted and now it will only let me change my resolution to 320x240 or 800x600...

---

### Post by Asheboy on 2008-08-01
Have you got your graphics card enabled? System>Admin>Hardware Devices.

If so, install envy and get that to install your nvidia drivers, should do the trick.

---

### Post by Existance0 on 2008-08-01
Hmm I have my nvidia drivers installed and I installed envy didn't seem to do anything. The program is called Envy24 Control right?

---

### Post by Asheboy on 2008-08-01
Yeah it is. Sorry that didn't help. I'm out of ideas :(.

---

### Post by Existance0 on 2008-08-01
Now whenever I reboot it tells me ubuntu is running in low graphics mode and makes me manually select what grapics card I have.

---

### Post by Existance0 on 2008-08-01
I'm tring to install the updated drivers but they give me a .run file if i execute it as a program it tells me I need root privlages if I try to run it using sudo it tells me it cant find the command...

---

### Post by Existance0 on 2008-08-01
Well I've installed 3 different drivers and things changed but resolution is still way to low 800x600, 640x480, 320x240.

---

### Post by Existance0 on 2008-08-01
nothing? :(

---

### Post by GS2 on 2008-08-01
Just of the top of my head - but has X Windows been reconfigured (or configured) to allow the different resolutions ?

---

### Post by tuxxy on 2008-08-01
You could try reconfigure xorg, and also you should be able enable the drivers without installing Envy

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Existance0 on 2008-08-01
Wow thanks It seemed I was using Nvidia xserver as default and for some reason that wouldn't let me go past 800x600 resolution. Although There isn't going to be any drawbacks to changing this is there?

---

### Post by tuxxy on 2008-08-01
Try it with some simple 3D games and your effects

---

### Post by slackusr on 2008-08-03
[https://help.ubuntu.com/community/DebuggingXAutoconfiguration]("https://help.ubuntu.com/community/DebuggingXAutoconfiguration")

But if you are like me you will get it fixed for a day (I also have a GeForce card and noticed that it doesn't seems like the best card for this OS), then during your next reboot, find the problems is right back in your face. Ironically **slackware** happened to find, and get the resolutions right the first time. 640x480 is just painful, and I really don't have the time to try and fix it every day that I need to use another OS.

---

