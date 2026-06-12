---
title: "is it possible to recover a lost partition?"
date: 2011-06-14
forum: Desktop Environments
---

### Post by rizos on 2011-06-14
I was trying to resize to the left the sdb5 partition where ubuntu is/was installed and things got messy. 

I lost the partition it was unallocated. 

next "cleverly" used livecd and reinstall ubuntu (thinking it was just like a repair the system thing) but instead ubuntu install from new...all my data is lost...gone with the wind.


i try sadly enough testdisk but it says partition corrupted impossible to recover.


now the whole disk shows as unallocated in gparted.


now im running ubuntu from a second hard drive and strange enough my windows 7 partition with files is save and sound.


i wonder if there is anything i can do to recover my files (guess the enitre partition now is lost)

i try photorec and no files were able to recover then try scalpel and it says files were not find or couldnt read the partition.


any idead will be appreciated.


of course "cleverly" i didnt had a recent back up of my files.


note* also now i cant access the new ubuntu partition that still in sdb5 at boot takes me directly to windows 7.

---

### Post by dabl on 2011-06-14
> **rizos said:**
> I was trying to resize to the left the sdb5 partition where ubuntu is/was installed and things got messy. 
.
.
.
i try sadly enough testdisk but it says partition corrupted impossible to recover.
.
.
.
now the whole disk shows as unallocated in gparted.
.
.
.
any idea will be appreciated.


That is a sad situation, and I'm afraid there is no recovery.  There is only the possibility of improved knowledge, and better tools for next time.

Make yourself a Parted Magic Live CD or USB stick:  [http://partedmagic.com/doku.php?id=downloads](http://partedmagic.com/doku.php?id=downloads)

Separate disk partitioning from installation of the OS.  Do your disk partitioning first, with attention to existing data partitions, and then use your Linux Live CD only to install an OS.

---

### Post by rizos on 2011-06-14
thanx starting from zero and now im kind of very well trained in what NOT to do and how to recover partitions in case this happens again.

now i try photorec but it just recover album cd artwork pictures.


but there a lots of info still some where i have the impresion that photorec cant access sdb5 partition owe to the fact that now holds my brand new (zero info on) partition encrypted.

is there a way to help photorec search in sdb5 partition with a passwrod??

---

### Post by GoGoThomas on 2011-06-15
Hi,

Your situation looks quite messy, the fact the encryption is involved and that you reinstalled the operating system does not help indeed (if you asked the OS install program to reformat the partition when reinstalling then it's even worse). It looks like a job for a specialist in data recovery management, they should be able to tell you if the data is recoverable or not and give you a quote. They are quite a few companies out there specializing in this kind of jobs.

HTH anyway.

---

