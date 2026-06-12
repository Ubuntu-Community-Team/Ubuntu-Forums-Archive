---
title: "why some many os chocies in my hard drive"
date: 2008-12-14
forum: General Help
---

### Post by sandman92 on 2008-12-14
how come when i go in to chose an os it has like 4 different ones i can go into for Ubuntu one of them is for recovery and one of just appeared after i installed some the updates i needed to install is their a way to take them off because im also using windows as secondary os 
is their a way to take off the other Ubuntu choices off the list

---

### Post by taurus on 2008-12-14
There should be a two entries for each kernel that you have on your machine: one for normal boot and one for recovery mode.  And if you have two kernels which I believe you do (one from original when you installed and a newer version), then you would have four entries.  It's always a good idea to keep a previous working kernel just in case the new one decides to take a vacation.  However, if you really want to remove those old entries, then you can edit /boot/grub/menu.lst and remove them from the list.

Applications -> Accessories -> Terminal
```
gksudo gedit /boot/grub/menu.lst
```
And if you want to remove the old kernel, you can search for it and delete it with synaptic.

p.s.  What happens to your other account?  Why did you create a new account, leaving out the last two digits?

---

### Post by logos34 on 2008-12-14
> **taurus said:**
> It's always a good idea to keep a previous working kernel just in case the new one decides to take a vacation.  However, if you really want to remove those old entries, then you can edit /boot/grub/menu.lst and remove them from the list.


+1

like taurus says it;s a good idea to keep the previous kernel.  If you don't want it cluttering up your grub menu screen, just comment out (**#**) each line so it doesn't show

---

### Post by sandman92 on 2008-12-14
thanks

---

### Post by sandman92 on 2008-12-14
another question should i upgrade to 8.10 is it worth it

---

### Post by logos34 on 2008-12-14
depends... read up on the improvements.  If you have anything that's not working, minor issues, etc. then maybe upgrading will fix them.  Personally, I normally can't wait to upgrade to the newest version, but this time I'm sticking with 8.04 because everything just works, and it's an LTS release.

---

