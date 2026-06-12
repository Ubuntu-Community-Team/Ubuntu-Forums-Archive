---
title: "partitions are not visible"
date: 2009-02-19
forum: General Help
---

### Post by kushal.7 on 2009-02-19
hi,
I am using ubuntu 8.10.
I used some wrong commands, due to lack of knowledge.
Now my windows partition ( c: ) is not visible in my computer.
now it can be opened through the /media.
but when i use "ls" from command prompt in media directory, then it give the following output.

ls: cannot open directory .: Transport endpoint is not connected

please help

---

### Post by kushal.7 on 2009-02-19
After my applying more commands, my other drive is giving problems.

when i tried open other drive,it is giving gollowing error

Could not display "/media/Softwares".
Error: Error stating file '/media/Softwares': Transport endpoint is not connected
Please select another viewer and try again.

& /media is also not visible.

Please help.

---

### Post by deepclutch on 2009-02-19
Is it a windows partition(other system) on a Network?
--
else ,
can you post the o/p of "sudo fdisk -l" from a terminal?it will display the partitions identified by GNU/Linux.
In ntfs filesystems ,sometimes if corrupted ,you need to use a tool "ntfsfix" and reboot to windows to run a file system check and fix .the format is "sudo ntfsfix /dev/sdx" without quotes.where /dev/sdx is the ntfs parition.

---

### Post by indytim on 2009-02-19
So what commands are you issuing and do you understand what they are supposed to be doing?

IndyTim

---

### Post by caljohnsmith on 2009-02-19
How about also posting the output of:
```
sudo fdisk -lu
```
And let us know which partition(s) you are trying to access.

---

### Post by kushal.7 on 2009-02-19
> **caljohnsmith said:**
> How about also posting the output of:
```
sudo fdisk -lu
```
And let us know which partition(s) you are trying to access.

Everythng solved after restart..

But only 1 problem left, that is when i restart there are no partition shown in /media
so not able to go to /media/"drive-name" through command line

but if i open any drive once by GUI, then that drive appears in /media, so able to open through that through command line.

I have to apply this procedure for all drives. These drive remains in /media till the session means after restart i have to do it.

---

### Post by konqueror7 on 2009-02-19
have your tried adding the partition to your fstab?

oh, also can you post the contents of it, so we could map the code,,,
```
sudo gedit /etc/fstab
```

---

### Post by kushal.7 on 2009-02-19
> **konqueror7 said:**
> have your tried adding the partition to your fstab?

oh, also can you post the contents of it, so we could map the code,,,
```
sudo gedit /etc/fstab
```

no, i don't know how to do it ?

the output is 
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/host/ubuntu/disks/root.disk /               ext3    loop,errors=remount-ro 0       1
/host/ubuntu/disks/boot /boot           none    bind            0       0
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0

---

### Post by konqueror7 on 2009-02-19
okay, type in the terminal...
```
fdisk -l
```
this will give you a table of your partition...

now lets try to add that partition manually to the boot...again in the terminal...
```
sudo gedit /etc/fstab
```

now add the lines...
```
[COLOR="Red"]/dev/sda1[/COLOR] [COLOR="Blue"]/media/Main[/COLOR] ntfs-3g defaults,locale=en_US.UTF-8 0 0
```
the red one is the partition you want to mount, its in the result of the *fdisk -l* command, and the blue one is where you want to mount it (create it woth root privileges)

now restart your machine (also, make a backup first of your fstab file)

---

### Post by kushal.7 on 2009-02-21
> **konqueror7 said:**
> okay, type in the terminal...
```
fdisk -l
```
this will give you a table of your partition...

now lets try to add that partition manually to the boot...again in the terminal...
```
sudo gedit /etc/fstab
```

now add the lines...
```
[COLOR="Red"]/dev/sda1[/COLOR] [COLOR="Blue"]/media/Main[/COLOR] ntfs-3g defaults,locale=en_US.UTF-8 0 0
```
the red one is the partition you want to mount, its in the result of the *fdisk -l* command, and the blue one is where you want to mount it (create it woth root privileges)

now restart your machine (also, make a backup first of your fstab file)

after aapling this command :

/dev/sda8 /media/Softwares ntfs-3g defaults,locale=en_US.UTF-8 0 0

nothing happens.... except that at booting time one line added in hundreds of line that "........... [Fail]"

---

### Post by kushal.7 on 2009-02-21
all drives working perfectly except the one "Softwares"

Now when i open the Software the following error occur:

Cannot mount volume.
You are not privileged to mount the volume 'Softwares'.

---

### Post by kushal.7 on 2009-02-21
1 more error :

Unable to mount location :
DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.

---

### Post by kushal.7 on 2009-02-22
pls somebody help

---

### Post by konqueror7 on 2009-02-22
type this in the terminal,
```
sudo fdisk -l
```

and please post the contents here...

---

### Post by kushal.7 on 2009-02-22
> **konqueror7 said:**
> type this in the terminal,
```
sudo fdisk -l
```

and please post the contents here...


I think that problem is related to privilage, as described in error. The output of above command is as follows: 

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe248e248

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1912    15356218+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1913       19456   140922180    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/sda5            1913        3824    15354328+   7  HPFS/NTFS
/dev/sda6            3825        8286    35840983+   7  HPFS/NTFS
/dev/sda7            8287       14023    46082421    7  HPFS/NTFS
/dev/sda8           14024       19456    43640541    7  HPFS/NTFS

---

### Post by konqueror7 on 2009-02-22
try forcing it to mount,
```
sudo mount -t ntfs-3g /dev/sda8 /media/Softwares -o force
```

---

### Post by kushal.7 on 2009-02-22
> **konqueror7 said:**
> try forcing it to mount,
```
sudo mount -t ntfs-3g /dev/sda8 /media/Softwares -o force
```

fuse: failed to access mountpoint /media/Softwares: No such file or directory

---

### Post by deepclutch on 2009-02-22
open terminal :
sudo mkdir /media/Softwares 
your problems with ntfs partitions ,I feel is due to some improper shutdowns with windows as well as Ubuntu?.make sure before rebooting/halting Ubuntu ,unmount your mounted ntfs partitions.It will be a good idea.
-
OK?
> DBus error org.freedesktop.DBus.Error.NoReply: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.
**What were you trying to accomplish when this error poped in?**
Try restarting dbus ,hal services:
```
sudo /etc/init.d/dbus force-reload
AND :
sudo /etc/init.d/hal force-reload

```

---

### Post by kushal.7 on 2009-02-22
> **deepclutch said:**
> open terminal :
sudo mkdir /media/Softwares 
your problems with ntfs partitions ,I feel is due to some improper shutdowns with windows as well as Ubuntu?.make sure before rebooting/halting Ubuntu ,unmount your mounted ntfs partitions.It will be a good idea.
-
OK?

**What were you trying to accomplish when this error poped in?**
Try restarting dbus ,hal services:
```
sudo /etc/init.d/dbus force-reload
AND :
sudo /etc/init.d/hal force-reload

```


sudo mkdir /media/Softwares 
this simply made a directory named software in /media, nothing happens...

I tried both commads as well nothing happens..

My main prob is I can't "even" open my drive by GUI b'coz of insufficient privilages, as i already posted the error

---

### Post by deepclutch on 2009-02-22
>  this simply made a directory named software in /media, nothing happens...then it is obvious that you have to do this ,as earlier it is complaining about non-existant /media/Softwares directory!huh:
sudo mount -t ntfs-3g /dev/sda8 /media/Softwares -o force

---

### Post by kushal.7 on 2009-02-22
> **deepclutch said:**
> then it is obvious that you have to do this ,as earlier it is complaining about non-existant /media/Softwares directory!huh:
sudo mount -t ntfs-3g /dev/sda8 /media/Softwares -o force

It was also my prob... but i think u didn't read the previous post (obviously not)....i told there that after applying this command 
```
sudo mount -t ntfs-3g /dev/sda8 /media/Softwares -o force
```
there was an error... but this got solved after applying ur previous command
```
sudo /etc/init.d/dbus force-reload
AND :
sudo /etc/init.d/hal force-reload

```
& then applying & then this command
```
sudo mount ....
```

anyways, THANKS A LOT !!!.... my prob got solved

---

### Post by deepclutch on 2009-02-22
if dbus,hal services are not starting at boot up ? anyways look at menu - system>preferences>session>startup>volume mount ->enable it.

---

### Post by kushal.7 on 2009-02-22
> **deepclutch said:**
> if dbus,hal services are not starting at boot up ? anyways look at menu - system>preferences>session>startup>volume mount ->enable it.

No option of volume mount is present there...

---

### Post by deepclutch on 2009-02-22
I mean search for "volume manager" - command is:
"/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable"

oh! make sure you have gnome-volume-manager installed.

---

### Post by kushal.7 on 2009-02-23
> **deepclutch said:**
> I mean search for "volume manager" - command is:
"/usr/lib/gnome-volume-manager/gnome-volume-manager --sm-disable"

oh! make sure you have gnome-volume-manager installed.

yes after installing it is visible thr & enabled.

THanks.

---

