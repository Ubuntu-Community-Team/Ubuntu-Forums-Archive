---
title: "New Xserver updates..."
date: 2006-08-22
forum: Desktop Environments
---

### Post by nzk on 2006-08-22
I am going to run automatix, will it update the xserver against my will? If that happens do I just type in the previous update?

Because I already did that


Am I safe?

How long until this madness ends?!


(This is on a clean install, that damn update destroyed my last install of ubuntu, same for the install before that, all on monday ](*,) ](*,) ](*,) )

---

### Post by r4ik on 2006-08-22
I would not run nothing for the moment specialy if unsure.
Just wait for a while until things clear up.
...my two cents...

---

### Post by kleuter on 2006-08-22
These new xserver updates just thrashed my Laptop ATi based install, so be very carefull!

---

### Post by r4ik on 2006-08-22
Just in case someone missed it,

[http://www.ubuntuforums.org/showthread.php?t=241254](http://www.ubuntuforums.org/showthread.php?t=241254)

---

### Post by joal on 2006-08-22
I just installed the Xserver update and it killed my x setup completely. No more GUI login... Now all I get is a: "Failed to load module libGLcore.so" error. (??)


It also deleted all my backup files in the /etc/X11 directory... I should have know better than to keep them there! And Ubuntu should know better than to give you X updates that destroys your previous configurations! :(

Does anyone have a working xorg.conf file to share.
I'm on a DELL PowerEdge SC 430 server, so no laptop configs please...

-j-

---

### Post by r4ik on 2006-08-22
Try,

sudo apt-get install xserver-xorg-core=1:1.0.2-0ubuntu10

sudo reboot

---

### Post by FuriousLettuce on 2006-08-22
You don't even have to reboot, you can just restart gdm (after downgrading X):

```
sudo /etc/init.d/gdm restart
```

---

### Post by utab on 2006-08-22
> **joal said:**
> I just installed the Xserver update and it killed my x setup completely. No more GUI login... Now all I get is a: "Failed to load module libGLcore.so" error. (??)


It also deleted all my backup files in the /etc/X11 directory... I should have know better than to keep them there! And Ubuntu should know better than to give you X updates that destroys your previous configurations! :(

Does anyone have a working xorg.conf file to share.
I'm on a DELL PowerEdge SC 430 server, so no laptop configs please...

-j-

I have just downloaded some updates this morning and then restarted and the system hangs on, but I may restrart in the safe mode. What were those shits that made the system like this ](*,)

---

### Post by micantox on 2006-08-22
> **utab said:**
> I have just downloaded some updates this morning and then restarted and the system hangs on, but I may restrart in the safe mode. What were those shits that made the system like this ](*,)

If it hangs during the boot phase, try to remove the splash option from the boot entry you choose. To do that:

- Press ESC when you have the opportunity to do so, to enter in grub menu
- Highlight the kernel line of interest
- press 'e' to edit the line
- choose the longest line (the one with the kernel exec file, should be vmlinux-...)
- press 'e' again
- delete the splash option
- press enter 
- press b to boot the kernel

Hope it helps.
Bye

---

### Post by joal on 2006-08-22
Thanks R4ik!

That worked! :) 
Downgrading the xserver-org-core...

However, the changes I made to xorg.conf remains. Could someone give me a link to some simple and useful **xorg.conf** description? I would like to know what all those GLcore,glx,dri modules does, and if I need them or not?? (I commented out those, and it still seem to work, perhaps I can comment out more...)

-j-

---

