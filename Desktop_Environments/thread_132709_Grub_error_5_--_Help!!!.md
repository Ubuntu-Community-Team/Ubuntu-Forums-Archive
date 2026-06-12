---
title: "Grub error 5 -- Help!!!"
date: 2006-02-18
forum: Desktop Environments
---

### Post by mmcmonster on 2006-02-18
Hi.
I was using partition magic under Windows to move a windows partition from hdb to hda, and now grub doesn't boot anything up.

I get an "error 5" in grub.

I'm currently booting off of a knoppix live CD, but don't know how to fix things up.

hda1 is my windows c: drive and appears to be intact.
hdd5 is my windows d: drive and appears to be intact.
hdd6 is my Ubuntu /home mount point and appears to be intact.
I can't seem to find my Ubuntu / or /usr mount points. (They used to be on hda in a logical partition, according to partition magic.)

Where do I start?

---

### Post by o_fortuna on 2006-02-18
[QUOTE=mmcmonster]Hi.
I was using partition magic under Windows to move a windows partition from hdb to hda, and now grub doesn't boot anything up.

I get an "error 5" in grub.

I'm currently booting off of a knoppix live CD, but don't know how to fix things up.

hda1 is my windows c: drive and appears to be intact.
hdd5 is my windows d: drive and appears to be intact.
hdd6 is my Ubuntu /home mount point and appears to be intact.
I can't seem to find my Ubuntu / or /usr mount points. (They used to be on hda in a logical partition, according to partition magic.)

Where do I start?[/QUOTE]
If you don't have / then you don't have anything. /boot is where GRUB is. If you could find where / is and where /boot is, you could follow the instructions in this wiki: [Recovering Ubuntu After Installing Windows]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?highlight=%28restore%29%7C%28ubuntu%29") It's pretty generic, and will help you fix GRUB, I think. Knoppix should be able to help you there too, if you can find /. Without that though, a reinstallation might be necessary (bad, but less so as your have /home mounted separately).

---

### Post by lha on 2006-02-19
[QUOTE=mmcmonster]Hi.
I was using partition magic under Windows to move a windows partition from hdb to hda, and now grub doesn't boot anything up.

I get an "error 5" in grub.

I'm currently booting off of a knoppix live CD, but don't know how to fix things up.

hda1 is my windows c: drive and appears to be intact.
hdd5 is my windows d: drive and appears to be intact.
hdd6 is my Ubuntu /home mount point and appears to be intact.
I can't seem to find my Ubuntu / or /usr mount points. (They used to be on hda in a logical partition, according to partition magic.)

Where do I start?[/QUOTE]

Run
```
sudo fdisk -l
``` It shows what's left of your partitions. If you need help to interpret the output, post results here. If you are missing a partition, [gpart]("http://www.stud.uni-hannover.de/user/76201/gpart/") might be able to guess where it was.

But I fear you are in *a lot* of trouble:

[Grub error] 5 : Partition table invalid or corrupt
    This error is returned if the sanity checks on the integrity of the partition table fail. This is a bad sign.

(Taken from [Grub manual]("http://www.gnu.org/software/grub/manual/grub.html"))

Partition Magic has caused grief to me, and it does look like it is your turn now. :(

---

