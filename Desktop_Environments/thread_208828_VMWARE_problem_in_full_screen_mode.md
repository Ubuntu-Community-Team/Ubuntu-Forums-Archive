---
title: "VMWARE problem in full screen mode"
date: 2006-07-04
forum: Desktop Environments
---

### Post by Dearhell on 2006-07-04
I have replaced the ATI drivers that Ubuntu install automatically with the ATI drivers from ATI website, but now I can't change to fullscreen mode in VMWARE, the screen displays this message: Out Of Range

It's a message directly from the display, not from Ubuntu or VMWARE

Any idea about this?

---

### Post by Dearhell on 2006-07-04
If I could know what file manage this thing, I can install Ubuntu Dapper again, see what the file has, and replace it when I install again the new ATI drivers.

---

### Post by Thund3rstruck on 2006-07-04
same thing happened to me but then I had a laptop with widescreen resolution. Try going into "quick switch" mode which is basically fullscreen mode. Works great for me

---

### Post by Dearhell on 2006-07-04
I have tested that quick switch mode but doesn't work as full screen mode in my Ubuntu, all it does it's put vmware window full screen, but the windows XP screen it's still shrink

---

### Post by Dearhell on 2006-07-05
I forgot to say that I'm using VMWARE Server, not VMWARE Player

---

### Post by Dearhell on 2006-07-08
Anyone knows what file manage the graphics configuration?

May be there is a backup in that directory and seeing differences between the new ATI drivers and those that come with Ubuntu, I could figure out what's going wrong with the new ATI drivers and VMWare full screen mode 

The full screen mode worked fine with the drivers that come with Ubuntu, but in Ubuntu the screen was frozen with the screensaver, so I have to change them with the new ones from ATI

---

### Post by bartbes on 2006-07-08
You mean the full screen in another X server? (Alt+Ctrl+F9 in most cases)? or another if the last try it..

---

### Post by Dearhell on 2006-07-08
The problem was clicking on the full screen option in the VMWare panel, in my own X session

[[IMG]http://img157.imageshack.us/img157/4430/pantallazowindowsxpprofessiona.th.png[/IMG]](http://img157.imageshack.us/my.php?image=pantallazowindowsxpprofessiona.png)

But I know what was wrong now, it has been fixed at last

The problem wasn't with the new ATI drivers as I thought, the problem was in the new resolution that was in the Windows system trough WMVare

It was at 800x600, but it seems that my TFT screen doesn't accept this resolution, I have changed that resolution with 1280x1024 and now all works fine

So the out of range message was displayed not because of the ATI drivers, it was displayed because of the resolution

---

