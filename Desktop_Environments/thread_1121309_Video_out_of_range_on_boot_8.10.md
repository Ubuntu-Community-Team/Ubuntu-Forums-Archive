---
title: "Video out of range on boot 8.10"
date: 2009-04-09
forum: Desktop Environments
---

### Post by Ericwt on 2009-04-09
Hi I have a problem when booting 8.10 says video is out of range hangs then completes boot. Need command to edit and change settings. 
                 H 44khx
                 V 84 Hz
            max 1280 x 1024
Setting is correct in display 1280 x 1024 at 60 hz

Thanks for your help

---

### Post by hictio on 2009-04-10
I don't understand completely, sorry.
You want to add, that is, to use those Vertical and Horizontal values?
If I understood correctly, you are already running at 1280x1024, is that right?

---

### Post by sylar30 on 2009-04-10
I have the exact same problem.  I installed 8.1 just today on an HP desktop with Vista Home Premium as the original OS and an HP V19 monitor.  Only after I log in does it correct itself.

---

### Post by Pasdar on 2009-04-10
You can go to safe graphics mode or go into command line and type: **xrandr -s resolution**, Example:
```
xrandr -s 1024x768
```

type **xrandr --help** to see all the available commands.

---

### Post by sylar30 on 2009-04-11
Thanks for the information.  I tried this command while inside Linux and it didn't help.  When I restarted it still told me "out of range  set to 1280x1024" until I logged in, then the monitor flickered and I was fine.  Please any other suggestions?  This is the only part of Linux that I cannot get to work properly (SO FAR)

> **Pasdar said:**
> You can go to safe graphics mode or go into command line and type: **xrandr -s resolution**, Example:
```
xrandr -s 1024x768
```

type **xrandr --help** to see all the available commands.

---

### Post by lisati on 2009-04-11
I had a similar problem on one of my machines, with the monitor complaining of a signal out of range while the splash screen should be showing. 
The way I dealt with it was to edit menu.lst and change the line that reads
> # defoptions=quiet splash
to read
```
# defoptions=quiet nosplash
```
and then from the terminal issue
```
sudo update-grub
```

An alternative is to tinker with the same line to set different video modes until you find one that works.

---

### Post by Ericwt on 2009-04-11
I solved the problem by installing Start Up Manager and changing the display to 1024 x 768 and then updating grub menu.lst . I installed Mint 6.0 and it did the same thing guess its a ubuntu thing. I am using a 19" flat screen monitor.
Thanks

---

### Post by sylar30 on 2009-04-12
I will definitely try your idea!!!  I'll try to find the Start up Manager and Mint 6.0 whatever those are.  

> **Ericwt said:**
> I solved the problem by installing Start Up Manager and changing the display to 1024 x 768 and then updating grub menu.lst . I installed Mint 6.0 and it did the same thing guess its a ubuntu thing. I am using a 19" flat screen monitor.
Thanks

---

### Post by sylar30 on 2009-04-12
I could not find Mint 6.0 on the downloadable sofware list.  I installed Update Manager and changed it to 1280x1024 then I got a message during the boot in the non-spash screen saying my video mode 31b was not a valid one.  ALl this crap just to get my monitor to know it's in an OK video mode when I get to the login screen.  Geez.

> **Ericwt said:**
> I solved the problem by installing Start Up Manager and changing the display to 1024 x 768 and then updating grub menu.lst . I installed Mint 6.0 and it did the same thing guess its a ubuntu thing. I am using a 19" flat screen monitor.
Thanks

---

### Post by Ericwt on 2009-04-12
Try 1024 x 768 see if that helps. Mint 6.0 is a a Ubuntu O S, I just installed it to if it did the same thing as Ubuntu 8.10.

Hope this helps

---

