---
title: "Automount of Removable Media under Kubuntu"
date: 2006-08-02
forum: Desktop Environments
---

### Post by Avian00 on 2006-08-02
I'm in the process of switching from Gnome (Ubuntu) to KDE (Kubuntu).  However, something I've come to depend upon from Ubuntu seems to be handled differently in Kubuntu.  I think I'm really talking about a difference between Gnome and KDE, but I'll continue to refer to them as Ubunut and Kubuntu, respectively.

In Ubuntu, when I attach a removable storage device (USB or FireWire), the system is nice enough to automount that device in /media under a sub-folder that is named after that drive's label.  For example, I have a drive named VMWARE (which contains all my virutal machines).  In Ubuntu, that drive automatically gets mounted every time to /media/VMWARE.  I've come to depend upon this predictability.

Kubuntu, on the other hand, chooses to mount the drive based upon its entry in the /dev folder.  So, using the above example again, if my VMWARE drive is the first drive attached, rather than mounting at /media/VMWARE, it mounts at /media/sda1 (which makes sense to me, I just don't like it).  Does KDE give me the option to change this behavior so it behaves like Ubuntu when I attach a removable drive?  Any help is much appreciated.

Thanks in advance,

Matt

---

