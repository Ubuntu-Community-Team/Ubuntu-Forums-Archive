---
title: "File permissions"
date: 2007-02-03
forum: Desktop Environments
---

### Post by RythmDivine on 2007-02-03
Second day of Ubuntu edgy...

**Problem**

I have 6 harddrives installed on the computer. There are a total of 9 partritions. I understand that these are owned by Root. I as a user have permission to read them, nothing more.

**Situation**

I can type in terminal

> gksudo nautilus 

and from there edit, copy, delete various files on different drives. But this seem a bit cumbersome to me. I would like a solution where i either can click the respective icons on the desktop and from there just copy/paste/delete files at will. Or be able to have a link (as in shortcut) on the desktop to nautilus with gksudo permission already active.

Thanks!

---

### Post by Waappu on 2007-02-03
Hi

This might help you

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_browse_files.2Ffolders_as_root_user_in_Nautilus)

---

### Post by Waappu on 2007-02-03
Hi

Or install Automatix2
[http://www.getautomatix.com/](http://www.getautomatix.com/)
there you can install nautilus scripts that create right-click context menu scripts to nautilus where you can find e.g. option "root-browse-here"-

From Automatix you can install also other useful programs

---

### Post by gradedcheese on 2007-02-04
> **RythmDivine said:**
> Second day of Ubuntu edgy...

I have 6 harddrives installed on the computer. There are a total of 9 partritions. I understand that these are owned by Root. I as a user have permission to read them, nothing more.



You can actually change that.  The file you want to edit (with sudo) is /etc/fstab  you can set options there as far as what permissions those portions are mounted with.  You can run 'man fstab' to read about the fstab format, but basically the <options> section of each partition determines the permissions (which you can change to 'user' for example).

---

### Post by aysiu on 2007-02-04
These two links should help:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

