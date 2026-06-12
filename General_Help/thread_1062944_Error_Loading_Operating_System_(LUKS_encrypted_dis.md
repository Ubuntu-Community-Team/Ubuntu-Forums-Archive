---
title: "Error Loading Operating System (LUKS encrypted disk)"
date: 2009-02-07
forum: General Help
---

### Post by pha3r0 on 2009-02-07
I might be totally screwed on this one I am not sure but heres what happened

I dropped in a second hard drive from my brothers dead PC and added an entry to the GRUB menu to boot it. When I rebooted and chose the new entry it did boot so I rebooted and got an "error loading OS" or something like that.

I dropped in my super grub disk and went through the steps. I have now tried every option on the disk under GNU/Linux boot to no avail.

Everytime I start it up I get the same "error loading OS" message.

I have the whole disk encrypted except my boot partition grub is listing 2 partitions but I know there to be 4 total

GRub lists hd0,0 as partiion type 0x6 and hd0,1 as being 0x7 which I take is because they are encrypted. 

Also in Gparted It shows one ext3 partition (would be boot) and one other of unknown type (this is my /home) and it shows the remaining space as unalocated, which scares me because that is the whole rest of my FS.

I will be monitoring this thread through out the day today and untill I get it running again

thanks in advance.

---

### Post by pha3r0 on 2009-02-07
bump, I have been looking around the net and I am not finding any useful information. I don't remember the exact steps I used when setting up the encryption but I know its a standard LUKS setup with PAM and I don't use any keyfiles or anything.

---

### Post by pha3r0 on 2009-02-07
bump

---

### Post by hyper_ch on 2009-02-07
(1) it's not polite to bump threads within 24h after your last post

(2) post the output of

```

sudo fdisk -l

```
and the content of your grub menu.lst

---

### Post by pha3r0 on 2009-02-08
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+   6  FAT16
/dev/sda2               7        7112    57078945    7  HPFS/NTFS


looking at this I question why either shows up as NTFS or FAT as this drive only had windows on it for a short time and it was totally wiped about a year ago for a fresh ubuntu only install

---

### Post by hyper_ch on 2009-02-08
do you have any other harddisks in there? and when pasting output enclose it in [noparse]```

```[/noparse] brackets.

---

### Post by pha3r0 on 2009-02-08
no other hard disks just the 400gig, Here is the output in ```
 brackets I don't think anything was filtered out though. 

[code]
Disk /dev/sda: 400.0 GB, 400088457216 bytes
255 heads, 63 sectors/track, 48641 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1           6       48163+   6  FAT16
/dev/sda2               7        7112    57078945    7  HPFS/NTFS

```

again thanks and I will try to monitor the thread more frequently we had a family outing planned today so I am just getting back to this now

---

### Post by hyper_ch on 2009-02-09
neither of them looks like luks encrypted devices or did you use wubi to install ubuntu?

---

### Post by pha3r0 on 2009-02-09
No i did not use wubi. It was a ubuntu 8.04 install disk. I setup dual boot first then removed windows and repartitioned with a clean install of ubuntu only a couple months later. 

I then went back and setup the encryption a short while after that.

It is odd to me that they are showing up as NTFS and FAT partitions and in Gparted it shows  EXT3 and an unknown.

---

### Post by hyper_ch on 2009-02-09
start up the live cd

instally cryptsetup
modprobe aes

there's a few more things needed but don't know right now

then try to open the disk by

```

sudo cryptsetup luksOpen /dev/sda2

```

---

### Post by pha3r0 on 2009-02-09
I installed cryptsetup and tried out some variations of your command (have to add a name to refer the the device as at the end of the line).
```

sudo cryptsetup luksOpen /dev/sda2 cryptohome

```
both sda1 and sda2 it tells me are not LUKS partitions.

modprobe is not available apt-get right now I am working on remiding that now

---

