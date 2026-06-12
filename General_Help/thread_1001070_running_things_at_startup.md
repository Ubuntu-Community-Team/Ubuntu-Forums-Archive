---
title: "running things at startup"
date: 2008-12-03
forum: General Help
---

### Post by csogilvie on 2008-12-03
I have Ubuntu 8.04 64-bit Desktop installed on a home machine that I mostly use as a light duty web-server.

It has an Asus P5Q motherboard, and sadly 8.04 requires that I recompile and re-install my network driver at each boot...  Once I do, it works fine for my purposes.  (I'm not interested in upgrading to ibex just yet... I tried and gnome exploded...  I'll wait another month before I try again)

I need to do a make, an make install, then an insmod to get the network driver going.

How do I put this into the startup scripts so if I ever need to restart it remotely, I'll be able to log back in once it comes back up?

Cheers.

---

### Post by csogilvie on 2008-12-17
Anybody?  

No clue why the network driver removes itself on re-boot...

Any help on this matter would be greatly appreciated!!!

---

### Post by Ayuthia on 2008-12-17
You shouldn't have to do the insmod at startup every time.  Have you tried copying the .ko file in /lib/modules/`uname -r`/?  I would just create a folder for it:
```
sudo mkdir /lib/modules/`uname -r`/mymodule
```
Then copy the .ko file into that directory.  You would then need to do the following:
```
sudo depmod -a
```
This will update the module dependency list.  You will most likely need to add the module to /etc/modules.

Hope that helps.

---

### Post by Ayuthia on 2008-12-17
> **csogilvie said:**
> Anybody?  

No clue why the network driver removes itself on re-boot...

Any help on this matter would be greatly appreciated!!!

It removes itself because you are using insmod with a self-compiled module.  Because of this, the system does not know anything about it.  The info in my last post will help the system see the module and adding the module to /etc/modules will let the system load the module when the system boots up.

---

