---
title: "Cannot Login: xsession-error"
date: 2005-10-19
forum: Desktop Environments
---

### Post by jeffreyvergara.NET on 2005-10-19
hello, I encountered this problem several times in Breezy Preview, and the only thing I can do is reinstall Ubuntu all over again thus erasing all my files. Now in Final Breezy release, I encountered it again, Im just lucky I created another administrator account.

Error:
Your session only lasted than 10 seconds... something like that

I tried the failsafe but I don't know the commands to fix it.

---

### Post by migueljacq on 2005-10-19
[QUOTE=jeffreyvergara.NET]hello, I encountered this problem several times in Breezy Preview, and the only thing I can do is reinstall Ubuntu all over again thus erasing all my files. Now in Final Breezy release, I encountered it again, Im just lucky I created another administrator account.

Error:
Your session only lasted than 10 seconds... something like that

I tried the failsafe but I don't know the commands to fix it.[/QUOTE]

I had a similar problem with hoary, it ended up being the way i set up my /home partition. can you post the contents of your /etc/fstab?

sudo gedit /etc/fstab

---

### Post by GrumpyBob on 2005-10-19
See [http://ubuntuforums.org/showthread.php?t=74841&highlight=ICEAuthority](http://ubuntuforums.org/showthread.php?t=74841&highlight=ICEAuthority)
(Among several similar threads)

Robert

---

### Post by somuchfortheafter on 2005-10-19
iceauthority made me quit using k3b it was to much of a hassle

---

### Post by jeffreyvergara.NET on 2005-10-19
here's my fstab:
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hdd        /media/cdrom1   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0
/dev/hdb1       /media/40GB  vfat    iocharset=utf8,umask=000   0       0


---

### Post by migueljacq on 2005-10-19
[QUOTE=jeffreyvergara.NET]here's my fstab:[/QUOTE]

my initial theory is that he needs a /home partition but i might be wrong?

EDIT: on second thought, I am wrong :)

---

### Post by jeffreyvergara.NET on 2005-10-19
[QUOTE=GrumpyBob]See [http://ubuntuforums.org/showthread.php?t=74841&highlight=ICEAuthority](http://ubuntuforums.org/showthread.php?t=74841&highlight=ICEAuthority)
(Among several similar threads)

Robert[/QUOTE]

deleting ICEAuthority worked! thanks! but why did this happen? I know I installed programs for Kde and it installed some files needed (k3b,amarok) so this might be the cause of that problem?

---

