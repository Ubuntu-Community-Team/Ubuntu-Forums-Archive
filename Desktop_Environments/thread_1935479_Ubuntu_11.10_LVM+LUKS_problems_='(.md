---
title: "Ubuntu 11.10 LVM+LUKS problems ='("
date: 2012-03-04
forum: Desktop Environments
---

### Post by cdd1985 on 2012-03-04
Hello all,

Im running an ubuntu 11.10 on Vmware Player 4


DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu 11.10"


And come here asking for help since i tried all and could not solve my problem. I have two LVM Volumes encrypted with LUKS and using /etc/init.d/cryptdisks to start disks at boot. The problem is during boot i get the following message:

[B]The disk drive for /mnt/mihome is not ready yet or not present.
Continue to wait, or Press S to skip mounting or M for manual recovery.[/B]

(( I thinks this is because the fstab is first checked without having yet the volumes opened (just a thougt)... ))
After this it will ask me for the passphrase BUT !! will actually **SHOW MY PASSPHRASE ON THE SCREEN !!!** =P , really crazy...

[[IMG]http://img6.imageshack.us/img6/3792/luksprob.jpg[/IMG]](http://imageshack.us/photo/my-images/6/luksprob.jpg/)

My config:

My crypttab:

[B]# <target name> <source device>         <key file>      <options>
mihome  /dev/mapper/vg-mihome   none    luks,noearly
miwww   /dev/mapper/vg-miwww    none    luks,noearly
[/B]
My fstab:

[B]# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda1 during installation
UUID=a0d6933c-e3c0-4fb3-a479-9859a5405f8b /               ext4    errors=remount-ro 0       0
# swap was on /dev/sda5 during installation
UUID=a2b8aa1f-5ab8-495c-9e62-3e253d3608d7 none            swap    sw              0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec,utf8 0       0
/dev/mapper/mihome      /mnt/mihome     ext4    defaults        0       0
/dev/mapper/miwww       /mnt/miwww      ext4    defaults        0       0
[/B]

Any idea on why is this happening ?
AFK:popcorn: hehehehehe

Thanks in advance .!

---

### Post by Flobbes on 2012-04-22
I have exactly the same problem.
Sadly it seems that nobody yet has a solution :/

---

