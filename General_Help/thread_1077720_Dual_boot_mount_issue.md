---
title: "Dual boot mount issue"
date: 2009-02-22
forum: General Help
---

### Post by davidself1001 on 2009-02-22
I have a dual boot (actually it's 4 OSs).  Windows XP and Windows 7 if improperly shut down will not allow me to mount my common NTSF partition.  Is there a way to override that issue when booting Ubuntu?  In fstab perhaps.  Below is my fstab content:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=3a0d8fe2-79b8-4836-91c4-11f403a8d1e2 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda7
UUID=123e6991-b719-4f7d-98e1-0b7b92ae5d2c none            swap    sw              0       0
/dev/sdb2 /home ext3 defaults,errors=remount-ro 0 1
/dev/sdb3 /media/Data ntfs defaults,errors=remount-ro 0 1
/dev/sdb1 /media/CWData ntfs-3g defaults,errors=remount-ro 0 1
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0

---

### Post by davidself1001 on 2009-02-22
Any ideas out there?

---

### Post by ajgreeny on 2009-02-22
I think you can add the force option to the lines for those partitions in the fstab.  You can certainly do that to a manual mount using the terminal, so I assume it will work in fstab as well.  However, why should this be needed?  Do you not always shutdown your windows system properly, or is it a result of system crashes?

---

### Post by davidself1001 on 2009-02-22
It is a result of Windows issues.  For example, this has only happened once so not sure it's an issue but Windows 7 after either going into sleep mode or hybernate mode followed by shutdown just hangs on shutdown for a long time and I finally did a hard reset to end it.  Then I couldn't mount when I can back up in Ubuntu.  I'll give the force option a try.  thanks for the help.  It's not like it will happen a lot but just in case it does I didn't want to have to restart back in Windows in order to clear up the problem.

---

### Post by ajgreeny on 2009-02-22
If it only happens occasionally, I suggest you do not use the force option in your fstab but force mount manually with the usual ntfs mount command.
```
sudo mount /dev/sda1 /media/windows/ -t ntfs -o nls=utf8,umask=0222,force
```Change the dev name etc as needed.  This may be safer than fstab edits.

---

### Post by davidself1001 on 2009-02-22
What is the risk in putting it in fstab?  Just for my understanding.

---

### Post by ajgreeny on 2009-02-23
I'm not really sure, but I have read somewhere that the force option can cause problems, even if it seldom does.  Also it seems a bit OTT to use that option when it is not needed.  Sorry I can't help more.

---

