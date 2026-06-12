---
title: "NFTS Partition Won't Show Up, but I can see it when I run sudo fdisk -l"
date: 2009-04-06
forum: General Help
---

### Post by Montreuxs on 2009-04-06
Hey all, I've just installed Ubuntu and I'm very new to linux but I like what I see so far. Ive only run into one problem. One of my NFTS partitions isnt showing up. My harddrive is partitioned into 4 sections, one for XP, one for Linux, one Media and one for Games. The media one is the one im haveing trouble getting into. When I run sudo fdisk -l the partition im talking about shows up as /dev/sda2 but I can't access it from my computer. 

Any help would be greatly appreciated and sorry if im missing something stupid as I said I'm very new to this

---

### Post by taurus on 2009-04-06
What happens if you run these commands to mount it by hand from a terminal?

Applications -> Accessories -> Terminal
```
sudo mkdir /media/sda2
sudo mount -t ntfs-3g /dev/sda2 /media/sda2
df -h
```

---

### Post by Montreuxs on 2009-04-06
it looks like that partition is haveing some type of hardware problem. is there any sort of check disk within Linux I could run because I cannot boot into my XP partition at this time.

> nick@nick-desktop:~$ sudo mkdir /media/sda2
mkdir: cannot create directory `/media/sda2': File exists
nick@nick-desktop:~$ sudo mount -t ntfs-3g /dev/sda2 /media/sda2
$MFT has invalid magic.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sda2': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.
nick@nick-desktop:~$ df -h

---

### Post by coffeecat on 2009-04-06
> **Montreuxs said:**
> is there any sort of check disk within Linux I could run because I cannot boot into my XP partition at this time.

There are some things you can do with the constituent utilities in ntfsprogs, but they're not really recommended as first-line repair tools for NTFS. For instance in man ntfsfix:

> ntfsfix  is a utility that fixes some common NTFS problems.  ntfsfix is
       NOT a Linux version of chkdsk.  It only repairs some  fundamental  NTFS
       inconsistencies,  resets  the  NTFS  journal file and schedules an NTFS
       consistency check for the first boot into Windows.You're far better off doing a chkdsk from Windows. What's the problem with booting into XP? If you have a real XP install disc (not an OEM restore image), you can boot into a repair console with that, and do a chkdsk from the Windows command line.

---

### Post by Montreuxs on 2009-04-06
Ill try that cause I do have a real xp install disc but I seem to be running into problems every step of the way with my computer lately, when I installed Linux my system wouldnt boot into xp anymore even when I booted into gparted and told told it to boot from that drive, but thanks for your help im gonna try what you said now.

---

### Post by Montreuxs on 2009-04-06
oh hell yea it worked. Thank you very much, the both of you.

---

