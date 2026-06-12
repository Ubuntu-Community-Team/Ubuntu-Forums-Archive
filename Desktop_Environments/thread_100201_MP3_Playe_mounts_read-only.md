---
title: "MP3 Playe mounts read-only"
date: 2005-12-07
forum: Desktop Environments
---

### Post by Oren on 2005-12-07
Hi all

I tried to search for the answer but I could not find a simillar query.
My MP3 player mounts fine and I can see it everywhere I am supposed to see it.
However, it mounts as read-only..... :???: 
Moreover, I am the owner and I have the read, write and execute all marked.
It is formatted to FAT. I am not sure what is going on? 
Nothing apears in 'fstab', so how do I make it read-write?

Do I have to mount it manualy?

Thanks, Oren

---

### Post by aysiu on 2005-12-07
Maybe you should put it in /etc/fstab, then. Do you know where it's located? Is it /dev/sda1? To be sure, plug it in and type ```
sudo fdisk -l
``` It'll usually be called something like /dev/sda1 or /dev/sde1.

```
sudo umount /dev/sda1
sudo mkdir /mp3_player
sudo cp /etc/fstab /etc/fstab_backup
```
I would add this line to /etc/fstab then: ```
/dev/sda1  /mp3_player   umask=000   0   0
``` Save. Unplug the device. Then plug it back in. Any luck?

---

### Post by Oren on 2005-12-08
Hi Aysiu and thanks for the reply.

I am not sure what happenned or what I did :???:  but it is all OK now.

To answer your q, the drive is /dev/sdb and when I plugged it in it did not show in fstab at all. But not to worry, it is working fine now....

Linux can be so weird.....:confused:

---

