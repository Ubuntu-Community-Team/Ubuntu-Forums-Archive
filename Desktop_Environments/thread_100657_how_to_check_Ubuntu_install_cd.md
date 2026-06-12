---
title: "how to check Ubuntu install cd"
date: 2005-12-08
forum: Desktop Environments
---

### Post by ShirishAg75 on 2005-12-08
Hi all,
      While one is installing Ubuntu the install program checks if the media is o.k. or has been corrupted. After installation if I wanna check if the CD as I've more than one copy of it is there any utility to check if the media is sound or not as I wanna share the copy with my friends & don't wanna give something which is corrupted somewhere or something. Thnx in advance.

---

### Post by fourchannel on 2005-12-08
you can use a program called md5sum to generate a unique signature for a file.

ok lets say you download the ubuntu.iso off the internet, and they give you the md5 key, ubuntu.iso.md5

once you download it you would run

```
md5sum ubuntu.iso
``` 
and then compare what you get with the ubuntu.iso.md5 key.

k, so your download went ok and you have a clean copy on your harddrive.

using your favorite burner program you make a CD out of the iso. (i like k3b, my burner of choice)

ok, now you want to test the actual cd to see if it burned correctly.

using a program called dd, you can remake a new iso out of the cd.

```
dd if=/dev/hdc of=ubuntu.iso_after_burn.iso
``` 
so now you have an iso from your cd, then you would check that file.

```
md5sum ubuntu.iso_after_burn.iso
``` 
and then compare that to the ubuntu.iso.md5 key.

if that passes then your cd was burned correctly.

---

### Post by ShirishAg75 on 2005-12-09
tht is informative but my issue is with the cd's which come from using ubuntu's shipit service. Does the same logic apply? Totally noOb here so while I was installing Ubuntu did it check only the md5 checksum or it also did a surface scan? Also where does the md5 checksum there on the cd itself. thnx in advance.

---

### Post by 5-HT on 2005-12-09
Thanks fourchannel for the tip on how to check a cd once burned, I've been using diff, but that requires me to check every folder and I never even thought to create an iso.


shirishag75, the same logic should apply. 
First off you can try to go to a server hosting the breezy iso to get the md5sum and check that against the cd using fourchannels advise.

Another thing is that I believe that the cd has md5sums already on it (just browse around the cd) which you can check, unfortunately I don't have a breezy cd handy at the moment to check exactly where they are kept.

From my limited knowledge of Ubuntu and linux though, I believe that .debs include checksums and that apt-get, and maybe even dpkg verify these during  installation, so if there's a problem it should let you know.

In terms of a surface scan, I don't think the installation would do so for the cd itself, but I really do not know.

HTH

---

### Post by oygle on 2005-12-27
[QUOTE=fourchannel]you can use a program called md5sum to generate a unique signature for a file.

ok lets say you download the ubuntu.iso off the internet, and they give you the md5 key, ubuntu.iso.md5

once you download it you would run

```
md5sum ubuntu.iso
``` 
and then compare what you get with the ubuntu.iso.md5 key.[/quote]

Can you please tell me where I might find md5sum for windows XP ?

Oygle

---

### Post by oygle on 2005-12-27
I'll try this one - [http://www.pc-tools.net/win32/md5sums/](http://www.pc-tools.net/win32/md5sums/)

---

### Post by stuporglue on 2005-12-27
You can also md5sum your cdrom device directly with the Ubuntu CD in it. I think you need sudo though since you're directly accessing a device. It saves on copy time though. 

$ sudo md5sum /dev/cdrom

---

### Post by cjj on 2006-07-11
Thanks, stuporglue:KS ! That's the info I was searching for (how to md5sum check a CD). 

-chris

---

