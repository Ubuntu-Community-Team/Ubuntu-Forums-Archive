---
title: "Mouse cursor invisible after upgrade"
date: 2010-10-11
forum: Desktop Environments
---

### Post by vckeating on 2010-10-11
Just upgraded to 10.10, which went smoothly except for the fact that my mouse pointer is now gone.  I can track where it is by ticking on the function that shows its location when you press control, but otherwise it's invisible (though technically functioning - I can still click on things and move it about).  

I've attempted to change the look of the mouse under theme in the hopes that it might be one that doesn't work, but after trying all of the selections I still haven't found one that will display.  

Any suggestions?

---

### Post by vckeating on 2010-10-12
In addition, I've just noted that the cursor 'comes back' if I suspend the machine and then bring it back.  There wouldn't be anything in the way this process works that might give a clue to why the cursor is gone at startup?

---

### Post by vckeating on 2010-10-12
Also, if it's any help, I've got the following video card:

```
VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
```

I've had to play with this in the past to get video working, so perhaps its in the same class of problems?

---

### Post by SteveDee on 2010-10-14
Yep, same graphic device, same problem and the same workaround: [http://ubuntuforums.org/showthread.php?t=1596288](http://ubuntuforums.org/showthread.php?t=1596288)

---

### Post by Bambabur on 2010-10-16
Dear guys,    the problem is in drm module in the kernel linux-image-2.6.35-22-generic provided with Ubuntu 10.10. 
To solve the problem, you can install another kernel from PPA :

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.35.7-maverick/)  

It worked for me!  

My video card is :  

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)  

Bye  

Bambabur

---

### Post by SteveDee on 2010-10-16
> **Bambabur said:**
> ...the problem is in drm module in the kernel linux-image-2.6.35-22-generic ...

Thanks for this idea, I tried the kernel you recommended and it fixes the mouse pointer problem, but I still have this problem: [http://ubuntuforums.org/showthread.php?t=1593960&page=2](http://ubuntuforums.org/showthread.php?t=1593960&page=2)
...and I get "Error: unable to locate IOAPIC" during boot.

So I'm sticking with kernel 2.6.32-25 for now.

---

