---
title: "[SOLVED] Dualboot Issue on Inspiron 1420N- Ubuntu Gutsy &amp;amp; Vista Home"
date: 2007-12-23
forum: Dell  Ubuntu Support
---

### Post by dnvikram on 2007-12-23
I have Gutsy installed on my 1420N Inspiron .I am trying to dualboot it with Vista Home,but I am not able to proceed with install as Vista says it cant use the unallocated space(20gb) and hence I have to abort the installation.Below is the current hard disk setup of my Gutsy machine:

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe8000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1459    11719386   83  Linux
/dev/sda2            1460        2116     5277352+  83  Linux
/dev/sda3            2117        3364    10024560   83  Linux
/dev/sda4            3365       12166    70702065    5  Extended
/dev/sda5            3365        4580     9767488+  83  Linux
/dev/sda6            4581        4823     1951866   83  Linux
/dev/sda7            5553        7984    19535008+  83  Linux
/dev/sda8            7985       10416    19535008+  83  Linux
/dev/sda9            4824        5552     5855661   83  Linux
/dev/sda10          10417       10440      192748+  83  Linux
/dev/sda11          10441       10683     1951866   82  Linux swap / Solaris
/dev/sda12          10684       12166    11912166   83  Linux


Filesystem             Size   Used  Avail Use% Mounted on
/dev/sda1               12G   316M    11G   3% /
varrun                 530M   193k   530M   1% /var/run
varlock                530M      0   530M   0% /var/lock
udev                   530M   140k   530M   1% /dev
devshm                 530M      0   530M   0% /dev/shm
lrm                    530M    36M   494M   7% /lib/modules/2.6.22-14-generic/volatile
/dev/sda12              13G   165M    12G   2% /backup
/dev/sda10             192M    24M   158M  14% /boot
/dev/sda2              5.4G   4.5G   584M  89% /home
/dev/sda9              6.0G   2.4G   3.3G  42% /misc
/dev/sda7               20G   181M    19G   1% /opt
/dev/sda6              2.0G    37M   1.9G   2% /tmp
/dev/sda3               11G   3.0G   6.7G  31% /usr
/dev/sda5              9.9G   1.1G   8.4G  11% /var
/dev/sda8               20G   8.8G    10G  47% /vmware


There is almost 20gb of unallocatd/unformatted space left on this hard drive,on which I want to install vista,then reconstruct grub and use easybcd to configure linux and vita as boot options.But,vista reports vista cannot use the available space .Can anybody tell y vista is behaving like that and how do fix that?

---

### Post by meierfra on 2007-12-23
Vista needs to be  installed on a primary partition. You can only have  four primary partition (sda1-sda4) and they are all used. So it is impossible to install Vista without some serious partitioning.

You could  increase the size of your extended partition (sda4), copy one or two  of your primary partition (sda1-sda3) to the extended partition,  delete whose  primary partitions and combine the unallocated space in one place.

---

### Post by Monkey_Tales on 2007-12-23
You first have to install vista and gutsy as last, because the bootloader will not recognise vista if you do it the other way around.

---

### Post by meierfra on 2007-12-23
> You first have to install vista and gutsy as last, because the bootloader will not recognise vista if you do it the other way around.

Installing Vista after Ubuntu also means that Vista will overwrite  Grub in the MBR. But that is not a big deal. Just reinstall Grub (see FixGrub in my signature) and add Windows to "menu.lst".

---

