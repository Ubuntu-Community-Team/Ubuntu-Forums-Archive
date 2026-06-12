---
title: "Absolute begginer SOS!!!"
date: 2009-06-24
forum: General Help
---

### Post by skiou on 2009-06-24
I recently installed ubuntu on my laptop, partitioning and dual booting keeping the existing XP.  However, the problems I come across running ubuntu seem to have no end. Firstly, when the update manager tries to install the updates a message shows up saying

[B]Not enough free disk space

The upgrade needs a total of 73.2M free space on disk '/'. Please free at least an additional 73.2M of disk space on '/'. Empty your trash and remove temporary packages of former installations using 'sudo apt-get clean'.
[/B]
Then , the same thing happens with Firefox, when I try to download anything 

[B]There is not enough room on the disk to save /tmp/m31sLX9+.package.part.

Remove unnecessary files from the disk and try again, or try saving in a different location.[/B]

However, when I try to change the destination folder the browse button doesnt work and even if I check the box that says to ask me where to save each time, the same thing happens.

Firefox seems to have addittional problems like the fact that I cannot use the previous/next page button or the google search toolbar but I suppose I need to reinstall it for linux (if only I could download anything)

I am at a complete loss. When I try to open the hard disk after a while the following message appears

[B]unable to  mount location.

DBus error org.gtk.Private.RemoteVolumeMonitor.Failed: An operation is already pending


[/B]Please help me..! I know I screwed up at some point of the installation process but I dont know where, I did it twice and I cant think of anything..

---

### Post by michy99 on 2009-06-24
It sounds like you didn't make your Ubuntu partition big enough. Open a terminal and run this command, then post the output here.```
sudo fdisk -l
```

---

### Post by tenach on 2009-06-24
How large is the root partition (often seen as "/")?  You may need to make your partition bigger.  I've had a similar problem, and most of the issues I had went away with making the root partition larger.

---

### Post by Celauran on 2009-06-24
> **skiou said:**
> Please help me..! I know I screwed up at some point of the installation process but I dont know where, I did it twice and I cant think of anything..

Sounds like you didn't create a large enough partition. Perhaps the simplest option at this point would be do re-do the installation and be sure to give Ubuntu enough room. I'd say 10GB is an absolute minimum.

---

### Post by pi.theta on 2009-06-24
It appears that all your problems could be related to the free space in your root partition. Can you check the total capacity of the root partition?

If its less then you need to increase it by using a suitable partition manager like gparted.

---

### Post by skiou on 2009-06-24
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xfe3afe3a

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       14267   114599646    7  HPFS/NTFS
/dev/sda2           14268       14593     2618595    5  Extended
/dev/sda5           14268       14571     2441848+  83  Linux
/dev/sda6           14572       14593      176683+  82  Linux swap / Solaris

---

### Post by LowSky on 2009-06-24
Did you install Ubuntu using Wubi?

---

### Post by skiou on 2009-06-24
no, I burned the disk etc..

---

### Post by merlinus on 2009-06-24
```

df -h

```will show partition size and usage.

---

### Post by michy99 on 2009-06-24
It looks like you only have about 2.5 gigs on your ubuntu partition. You definitely need more.

---

### Post by Leslie Viljoen on 2009-06-24
Would you mind posting the output of "df -h" too?

---

