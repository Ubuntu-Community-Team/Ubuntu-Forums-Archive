---
title: "automount for pendrive, CD, ...doesn't work"
date: 2008-10-19
forum: Desktop Environments
---

### Post by sandro54 on 2008-10-19
Hi evrybody

The problem is I cannot see from desktop the devices Pendrive, CD and HD Volume. I checked everything (HAL & related) and they seem OK.
When I use Konqueror/Dolphin  to access my data , the errore message I took is <feature available only with HAL>. Other message maybe related from X.Org Log is <   information   [config/hal] couldn't initialise context: (null) ((null))>.
The manual Mount works for PenDrive and CD.
My fstab is: 
```

xgrass@Kid:/$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda4
UUID=e39be3ca-c398-42c1-9507-15af0eb21a85 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=3A5821255820E17D /media/sda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda2
UUID=667C231E7C22E88F /media/sda2     ntfs    defaults,umask=007,gid=46 0       1
# /dev/sda3
UUID=fca8eb0c-1d32-459e-b787-e7a28faf4404 none            swap    sw              0       0
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
xgrass@Kid:/$                                            

```
my environment is:
```

[B]Kubuntu 8.04
Linux 2.6.24-21 generic
KDE version 3.5.10[/B]

```

Could anyone please help me   ??
Thanks in advance.

---

