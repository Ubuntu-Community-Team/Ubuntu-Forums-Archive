---
title: "Recovery From External HD in Ubuntu 14.04"
date: 2015-09-21
forum: Desktop Environments
---

### Post by dshock on 2015-09-21
I backed up my files on my ubuntu 12.04 machine before my mobo fried. I have another machine running 14.04 & I can mount the HD from the old machine as an external drive However, I can't see or copy contacts in kaddress book. The seperate files in their folders were saved & copied but how do I recover my address book?

---

### Post by sudodus on 2015-09-21
Probably the external drive is seen, but the partitions on it are not mounted.

Please post the output of the following commands in a terminal window (copy and paste it into a reply here and put it within [noparse]```
tags
```[/noparse]. It would help us help you.

```
sudo lsblk -fm
```

```
df
```

---

### Post by dshock on 2015-09-21
```
 dennis@dennis-GA-MA78GM-US2H:~$ lsblk -fm
NAME   FSTYPE LABEL MOUNTPOINT              NAME     SIZE OWNER GROUP MODE
sda                                         sda    232.9G root  disk  brw-rw----
&#9500;&#9472;sda1              /                       &#9500;&#9472;sda1 227.4G root  disk  brw-rw----
&#9500;&#9472;sda2                                      &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5              [SWAP]                  &#9492;&#9472;sda5   5.5G root  disk  brw-rw----
sdb                                         sdb     74.5G root  disk  brw-rw----
&#9500;&#9472;sdb1                                      &#9500;&#9472;sdb1   100M root  disk  brw-rw----
&#9492;&#9472;sdb2                                      &#9492;&#9472;sdb2  74.4G root  disk  brw-rw----
sdc                                         sdc    232.9G root  disk  brw-rw----
&#9500;&#9472;sdc1                                      &#9500;&#9472;sdc1     2G root  disk  brw-rw----
&#9500;&#9472;sdc2                                      &#9500;&#9472;sdc2    20G root  disk  brw-rw----
&#9492;&#9472;sdc3                                      &#9492;&#9472;sdc3 210.9G root  disk  brw-rw----
sdi                                         sdi    149.1G root  disk  brw-rw----
&#9500;&#9472;sdi1              /media/dennis/fcc80ba2- &#9500;&#9472;sdi1 143.5G root  disk  brw-rw----
&#9500;&#9472;sdi2                                      &#9500;&#9472;sdi2     1K root  disk  brw-rw----
&#9492;&#9472;sdi5                                      &#9492;&#9472;sdi5   5.6G root  disk  brw-rw----
sr0                                         sr0     1024M root  cdrom brw-rw----




dennis@dennis-GA-MA78GM-US2H:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1      234557280 11534620 211084716   6% /
none                   4        0         4   0% /sys/fs/cgroup
udev             2832568        4   2832564   1% /dev
tmpfs             568436     1372    567064   1% /run
none                5120        0      5120   0% /run/lock
none             2842176      156   2842020   1% /run/shm
none              102400       48    102352   1% /run/user
/dev/sdi1      147948700 20920016 119490268  15% /media/dennis/fcc80ba2-4b18-40ed-b0a1-f11b917adfb2
dennis@dennis-GA-MA78GM-US2H:~$
```

---

### Post by sudodus on 2015-09-21
> **dshock said:**
> ```
 dennis@dennis-GA-MA78GM-US2H:~$ lsblk -fm
NAME   FSTYPE LABEL MOUNTPOINT              NAME     SIZE OWNER GROUP MODE
sda                                         sda    232.9G root  disk  brw-rw----
&#9500;&#9472;sda1              /                       &#9500;&#9472;sda1 227.4G root  disk  brw-rw----
&#9500;&#9472;sda2                                      &#9500;&#9472;sda2     1K root  disk  brw-rw----
&#9492;&#9472;sda5              [SWAP]                  &#9492;&#9472;sda5   5.5G root  disk  brw-rw----
sdb                                         sdb     74.5G root  disk  brw-rw----
&#9500;&#9472;sdb1                                      &#9500;&#9472;sdb1   100M root  disk  brw-rw----
&#9492;&#9472;sdb2                                      &#9492;&#9472;sdb2  74.4G root  disk  brw-rw----
sdc                                         sdc    232.9G root  disk  brw-rw----
&#9500;&#9472;sdc1                                      &#9500;&#9472;sdc1     2G root  disk  brw-rw----
&#9500;&#9472;sdc2                                      &#9500;&#9472;sdc2    20G root  disk  brw-rw----
&#9492;&#9472;sdc3                                      &#9492;&#9472;sdc3 210.9G root  disk  brw-rw----
sdi                                         sdi    149.1G root  disk  brw-rw----
&#9500;&#9472;sdi1              /media/dennis/fcc80ba2- &#9500;&#9472;sdi1 143.5G root  disk  brw-rw----
&#9500;&#9472;sdi2                                      &#9500;&#9472;sdi2     1K root  disk  brw-rw----
&#9492;&#9472;sdi5                                      &#9492;&#9472;sdi5   5.6G root  disk  brw-rw----
sr0                                         sr0     1024M root  cdrom brw-rw----
```

You forgot sudo, which cripples the output. Please post the output of 

```
sudo lsblk -fm
```
> 

```
dennis@dennis-GA-MA78GM-US2H:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda1      234557280 11534620 211084716   6% /
none                   4        0         4   0% /sys/fs/cgroup
udev             2832568        4   2832564   1% /dev
tmpfs             568436     1372    567064   1% /run
none                5120        0      5120   0% /run/lock
none             2842176      156   2842020   1% /run/shm
none              102400       48    102352   1% /run/user
[COLOR="#FF0000"]/dev/sdi1      147948700 20920016 119490268  15% /media/dennis/fcc80ba2-4b18-40ed-b0a1-f11b917adfb2
[/COLOR]dennis@dennis-GA-MA78GM-US2H:~$
```

Do you have any idea in which drive (and partition) to find the contacts in your kaddress book? The first step is to mount that partition. Now the only mounted partition is

```
/dev/sdi1      147948700 20920016 119490268  15% /media/dennis/fcc80ba2-4b18-40ed-b0a1-f11b917adfb2
```

The next step is to identify the file where it is stored. Since the name is kaddress, I'm thinking of KDE. Are you running Kubuntu or standard Ubuntu? What application program does the address book belong to?

I don't know the solution to this second step, and I hope someone else can chip in and help you :-)

---

### Post by dshock on 2015-09-21
This IS the output of the sudo command. The HD is sdi and the partition is probably sdi1. I'm running Ubuntu 14.04 LTS with some KDE apps.

---

### Post by sudodus on 2015-09-22
OK

Try to find out about kaddress - where it stores its data. A guess is a file name with 'kaddress' as part of the name somewhere in your home directory under .config or .kde. [COLOR="#800080"]I hope someone who is using Kubuntu or at least KDE can chip in and help you.[/COLOR]

---

