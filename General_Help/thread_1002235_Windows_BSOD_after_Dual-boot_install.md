---
title: "Windows BSOD after Dual-boot install"
date: 2008-12-04
forum: General Help
---

### Post by Aralhach on 2008-12-04
I just got through the clean re-install, without putting a boot partition at the front (and it worked fine, this computer is crazy).  Anyway, I got Windows to boot now (it shows the WinXP Professional little logo with the blue lines moving at the bottom, but then gives me a BSOD with the following code:
```
STOP: 0x0000007B (0xF9683640,0xC000000E,0x00000000,0x00000000)
```

I've tried to boot into safe mode, safe mode with command prompt, and all the other options included in the menu, but when it loads a certain driver (something like agp440.sys) it shows the BSOD.  I booted with the CD into a recovery console and with chkdsk it says "The volume appears to contain one or more unrecoverable problems."

Any ideas?? :D

---

### Post by alzie on 2008-12-04
This appears to be a known issue with XP:
> 
This issue may occur if Windows XP tries to use an incompatible motherboard chipset video driver during startup. 

[http://support.microsoft.com/kb/324764](http://support.microsoft.com/kb/324764)

This page also gives directions on how to disable the misbehaving driver.

I hope this helps

---

### Post by Aralhach on 2008-12-04
Well, it wasn't the problem really.  It was due to a "bad" hard drive.  It said there was some unrecoverable errors. I'm just reformatting and will probably just have to leave it with Windows and give up trying to install Linux on it.  It looks like the computer just won't take it (I've tried several times already and there's just error after error, the error each time being different).

Thanks for your time and answers!!

---

### Post by Sealbhach on 2008-12-04
You could still try Wubi install. Install Ubuntu as if it were a windows application.

[http://wubi-installer.org/](http://wubi-installer.org/)


.

---

