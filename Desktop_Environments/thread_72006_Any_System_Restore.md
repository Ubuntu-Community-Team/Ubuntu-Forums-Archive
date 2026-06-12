---
title: "Any System Restore"
date: 2005-10-04
forum: Desktop Environments
---

### Post by Sirin on 2005-10-04
Hello, I'm just wondering, Is there any system restore, just in case I accidentally do something that mucks up the system? I was using Fedora Core 1, and everytime something messed up, I had to do a complete reinstall. Windows XP and ME has this feature, and I wanted to know if Ubuntu has it, or is planning to have it in the future?
(BELOW - The Windows XP System Restore Feature)
[IMG]http://winxp.uwaterloo.ca/Images/System_Restore_files/image001.jpg[/IMG]

---

### Post by banadushi on 2005-10-05
Well, kinda, but its not as easy as it is in Windows.  You can setup your root (/) filesystem on an LVM system and do LVM snappshotting of the partition.  Then you can roll back to any snapshot.

Have a good one!

---

### Post by skoal on 2005-10-05
Also, there's a substantial core difference between installing a Windows OS and linux.  We have packages and config files (either in /etc or the /home/<user> directory).  If you ever want to rollback a certain feature, whether Xorg or even coreutils, it's a simple matter of installing that package version (sometimes by a remove then a version force).  Since the package maintainers here handle that pretty good, even changing desktops is a snap.  Check out synaptic...

\\//_

---

