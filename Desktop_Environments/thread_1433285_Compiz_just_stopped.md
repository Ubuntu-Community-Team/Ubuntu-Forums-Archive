---
title: "Compiz just stopped?"
date: 2010-03-18
forum: Desktop Environments
---

### Post by Utsukushii Tsubasa on 2010-03-18
alright, so i was bored and started fooling around with the settings on compiz manager. as i went to rotate my cube [alt+ctrl+button1] nothing happens, so i make sure everthing is turned on properly, and it is, so i try again. nothing. then i tried making sure that visual effects were enabled, they werent. so i turned them on high to see if they worked. it searched then loaded, my screen flickered and said they could not be enabled. this isnt the first time this has happened. if someone knows why it does this, and how to fix it, please PLEASE tell me. running ubuntu jaunty

---

### Post by MelDJ on 2010-03-19
what graphic card do you have?

---

### Post by Henery on 2010-03-19
Same problem here might try back a version I have a nivida 8600gt 256mb it worked before so I know its capable just a bug of some sort!

---

### Post by Utsukushii Tsubasa on 2010-03-19
unfortunately its a little older, (and untill i can get a job it will remain that way) but its a NVIDIA GeForce 6100 graphics card. it always seems to work perfectly for a while, then STOP. i cant enable the driver or anything. but my resolution doesnt go back to the 800x600. only thing that stops is the ability to use compiz and enable the driver for desktop effects.

---

### Post by Henery on 2010-03-19
I don't know if it will work for you but I just downloaded and installed the latest nvidia driver 195.36.15 and now I can use the extra effects and compiz works again!

Here is a link to a how to install the latest drivers good how to helped me big time!
```
http://ubuntuforums.org/showthread.php?t=990978
```

---

### Post by Utsukushii Tsubasa on 2010-03-19
Well, i would like to say thanks for the link, and followed it to how you specified, unfortunately, it did not bring back my compiz settings, nor would it allow me to re-enable my desktop effects. any more ideas?

---

### Post by Henery on 2010-03-19
Well did the drivers install properly? If they did and you still can't enable desktop effect then I am out of ideas maybe a guru here will help ya!

---

### Post by Utsukushii Tsubasa on 2010-03-21
yes, everything was installed properly before hand as well, but it still will not allow me to enable them. and who is guru?

---

### Post by soltanis on 2010-03-21
Compiz is unstable and so crashes often, sometimes breaking different settings as it does so.

Try running

```

compiz --replace

```

In a terminal.

In general Compiz doesn't require a high end graphics card to work, but it does require that you have 3D acceleration which means if you have nVidia or ATI cards you should get the proprietary drivers which have that support.

Check under Hardware Drivers that not only are they installed, but that they are loaded and running.

---

### Post by Utsukushii Tsubasa on 2010-03-21
unfortunately i get loads of errors through that way and cannot change my resolution, so i have to follow a different method, they show up, then when i try to install anything above i believe 173, i only get a white bar above my screen when i try to login, and i cant see anything, so that doesnt work, after that i dont know how to check if theyre working. this is what i get when i run that command.
```
Checking for Xgl: not present. 
/usr/bin/compiz.real (core) - Error: Could not acquire compositing manager selection on screen 0 display ":0.0"
/usr/bin/compiz.real (core) - Fatal: No manageable screens found on display :0.0
Window manager warning: Invalid WM_TRANSIENT_FOR window 0x28000ef specified for 0x28000ce ().
```

---

### Post by Utsukushii Tsubasa on 2010-03-21
alright, i got it back up. i found this,
```
http://ubuntuforums.org/showthread.php?t=799070
```
 and well, yeah. anyway, after running this, letting it see what was wrong, allowing it to fix it, and running compiz in the terminal, it started working again. thanks for help though.

---

