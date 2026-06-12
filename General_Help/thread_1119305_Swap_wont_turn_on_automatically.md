---
title: "Swap wont turn on automatically"
date: 2009-04-07
forum: General Help
---

### Post by Dr Belka on 2009-04-07
I am having a problem with my swap partition.  It wont automatically turn on.  When I go into the gnome partition editor from the desktop, I can select the swap partition and "swapon" it, but I want ubuntu to do it automatically on startup. 

Anyone?

---

### Post by ryanhaigh on 2009-04-07
To have swap enabled at startup there has to be an associated entry in /etc/fstab. If you post the current contents of that file it should be pretty easy to determine whether it is enabled or not.

---

### Post by Dr Belka on 2009-04-07
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=fbab27fc-af55-451e-a361-5b593e6f7c49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a6a50703-1855-4211-81c2-212e878918f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I recently resized and its still not working

---

### Post by JC Cheloven on 2009-04-07
> **Dr Belka said:**
> # /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda5
UUID=fbab27fc-af55-451e-a361-5b593e6f7c49 /               ext3    relatime,errors=remount-ro 0       1
# /dev/sda6
UUID=a6a50703-1855-4211-81c2-212e878918f9 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0


I recently resized and its still not working

Probably the UUID of the swap partition is incorrect. To see this, can you please post the output of
```
sudo blkid
```

---

### Post by Dr Belka on 2009-04-07
/dev/sda1: UUID="2A38FDC038FD8AD9" LABEL="PQSERVICE" TYPE="ntfs" 
/dev/sda2: UUID="2CBABF41BABF05FC" LABEL="OS" TYPE="ntfs" 
/dev/sda3: UUID="2ECA38BB0DAFEEAE" LABEL="Storage" TYPE="ntfs" 
/dev/sda5: UUID="fbab27fc-af55-451e-a361-5b593e6f7c49" TYPE="ext3" 
/dev/sda6: TYPE="swap" UUID="ff381bef-a608-4aea-b506-6333915b7a94" 
/dev/sdb1: SEC_TYPE="msdos" LABEL="486MiB fat" UUID="499F-8664" TYPE="vfat"

---

### Post by ryanhaigh on 2009-04-07
As you can see the swap UUID you got from that last command doesn't match the one in /etc/fstab. You can edit the /etc/fstab entry so that it matches the real UUID of the partition and then it should mount swap every boot.

Use alt-f2 to bring up the run dialog then:
```
gksudo gedit /etc/fstab
```

Did you resize some of your partitions or something?

---

### Post by Dr Belka on 2009-04-07
i mentioned that i did resize the partiton

---

### Post by Dr Belka on 2009-04-07
Alright, i edited the file and restarted and it worked.  Thank you all very much.

---

### Post by JC Cheloven on 2009-04-08
> **Dr Belka said:**
> Alright, i edited the file and restarted and it worked.  Thank you all very much.

You're welcome ;-)

---

### Post by green0eggs on 2009-08-31
Thank you JC Cheloven, I had this exact same issue after messing around resizing my partitions. It is now resolved.

---

