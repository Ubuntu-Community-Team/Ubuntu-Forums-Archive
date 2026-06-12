---
title: "Dual-Boot"
date: 2009-05-22
forum: General Help
---

### Post by Flexico on 2009-05-22
Is there a way to set up grub to run two operating systems simultaneously (like partitioning the RAM or something similar, with the processor dedicated to just one at a time), and just switch between them with something like Ctrl-Alt-Shift-Delete?

---

### Post by raymondh on 2009-05-22
> **Flexico said:**
> Is there a way to set up grub to run two operating systems simultaneously (like partitioning the RAM or something similar, with the processor dedicated to just one at a time), and just switch between them with something like Ctrl-Alt-Shift-Delete?

Virtualization.   Load Ubuntu and then load your favorite virtualization program and run the other OS from there.  Ram will be shared whilst processor is dedicated to the particular OS you are operating with at the moment.  Shifting OS' is a matter of keystrokes (or mouse actions) as well.

Regards,

---

### Post by Flexico on 2009-05-23
> **raymondhenson said:**
> Virtualization.   Load Ubuntu and then load your favorite virtualization program and run the other OS from there.  Ram will be shared whilst processor is dedicated to the particular OS you are operating with at the moment.  Shifting OS' is a matter of keystrokes (or mouse actions) as well.

Regards,

I've tried using VirtualBox before, but it seemed to make Windows run very slowly. Also, is there a way to take an existing Windows install and put that into V-box?

---

### Post by raymondh on 2009-05-23
> **Flexico said:**
>  Also, is there a way to take an existing Windows install and put that into V-box?


Hello Flexico,

A bit complicated from what I read.  Given my limited knowledge, I found it easier to install XP rather than move XP into virtualbox.   Please see this link.

[http://www.virtualbox.org/wiki/Migrate_Windows](http://www.virtualbox.org/wiki/Migrate_Windows)

As for the "responsiveness" of the guest OS (XP, in my case), I cannot complain as my use of XP is already limited to a few functions only.  Nevertheless, I still allocated 2GB RAM for the XP guest which may be a little too much.  I have not used virtual XP for gaming nor have I had any benchmark tests done.  If it matters any, my card is an ATI HD 2400.

Have you looked at other virtualization alternatives/applications?

Regards,

---

