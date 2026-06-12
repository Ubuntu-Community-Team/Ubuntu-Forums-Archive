---
title: "Windows FS vs. Linux FS --Why?"
date: 2011-02-10
forum: Desktop Environments
---

### Post by NTWired on 2011-02-10
Hi,
I'm looking for more info about File Systems usage and hopefully this is the right place for it.
My question is about Differences in Filesystem-readings between Windows OS and Linux OS.

I'll provide an example:
Let's say i have a computer with SATA-HD with 2 NTFS Partitions when 1 of those Partitions has a Windows XP Pro installed.
At some point the booting process fails, and there's no reading of the partitions.

Using a USB2SATA cable i plugged the HD to a different computer also with windows XP to try and recover the data - Failure...can't see the partitions.
Then i used a bootble USB Mini-Windows --> same result.
I scanned the HD with MHDD >>It is 100% Fine.


At last i used Ubuntu from a USB and i was able to read everything that disk had on and recover my data.

So my questions are as such:
1.What is making linux better than windows in this matter?(technical information will be very much applaud).
2.Is it something to do with Reading process of the NTFS MBR? does linux read it differently?

10x:)

---

### Post by SivaCoHan on 2011-02-10
TRY IDE2SATA
some computers doesn't accept SATA some doesn't

---

### Post by NTWired on 2011-02-10
huh?
i don't have an actual "problem".
as i said, i can read and recover the data with linux - no changes made.


My question was "Why" linux can read the NTFS partitions while windows fails to...:)

---

### Post by ankspo71 on 2011-02-10
Hi,
Are we allowed to guess? :D I think when windows mounts a drive, it looks for windows filesystem specific data, such as MFT and VOLUME and other [_metafiles_]("http://en.wikipedia.org/wiki/NTFS#Metafiles") as if windows was expecting to find a working windows disk. I think in Linux and Dos, and probably many other systems, most of that windows specific data is ignored.

Ntfs is not a native filesystem type for Linux, and Linux actually does have some difficulty with Ntfs, or at least it used to. Here is one article explaining what it was like before the NTFS-3G driver for Linux came along: [http://bisqwit.iki.fi/story/howto/ntfs/](http://bisqwit.iki.fi/story/howto/ntfs/) Here's more info concerning Linux support for Ntfs: [http://en.wikipedia.org/wiki/NTFS#Linux](http://en.wikipedia.org/wiki/NTFS#Linux) (Note the part where it says "Note that all three userspace drivers..." too.

---

### Post by asmoore82 on 2011-02-10
Another *guess* …
The ACL "permissions" (Access Control Lists) on the NTFS volume could be
completely bork'd. Linux naturally ignores this data anyway.

---

