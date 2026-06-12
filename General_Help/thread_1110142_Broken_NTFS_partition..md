---
title: "Broken NTFS partition."
date: 2009-03-29
forum: General Help
---

### Post by Gabt on 2009-03-29
Hey, 

Got a problem here, i have a hard disk that i use for storing music and the likes of in. I was resizing the partition the other day and during the resize the power was cut off ! :<

I cant mount it at all, tried using testdisk to recover it, but cant seem to manage it. It definetley hasnt been formatted, so the data is still there, i'd like to be able to get the data back. Any help?

out put from trying to mount the drive:
```
:~$ sudo mount /dev/sdb1
Incomplete multi sector transfer detected in $MFT.
Failed to load $MFT: Input/output error
Failed to mount '/dev/sdb1': Input/output error
NTFS is either inconsistent, or you have hardware faults, or you have a
SoftRAID/FakeRAID hardware. In the first case run chkdsk /f on Windows
then reboot into Windows TWICE. The usage of the /f parameter is very
important! If you have SoftRAID/FakeRAID then first you must activate
it and mount a different device under the /dev/mapper/ directory, (e.g.
/dev/mapper/nvidia_eahaabcc1). Please see the 'dmraid' documentation
for the details.

```
fdisk
```
:~$ fdisk /dev/sdb

Unable to open /dev/sdb
:~$ fdisk /dev/sdb1

Unable to open /dev/sdb1

```

Any help would be greatly appreciated!!

thanks.

---

### Post by Gabt on 2009-03-29
Anyone know? :<

---

### Post by hyper_ch on 2009-03-29
open it in windows and then check it there. That should fix it.

---

### Post by Gabt on 2009-03-29
I dont has a windoes :(

---

### Post by Slim Odds on 2009-03-29
Install ntfsprogs and run ntfsfix

---

### Post by markharding557 on 2009-03-29
you have real problems,the only data recovery software i am aware of runs on...you guessed it windows.

---

### Post by Slim Odds on 2009-03-29
> **markharding557 said:**
> you have real problems,the only data recovery software i am aware of runs on...you guessed it windows.

You don't get around much.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by Gabt on 2009-03-29
> **Slim Odds said:**
> Install ntfsprogs and run ntfsfix
```
:~$ sudo ntfsfix /dev/sdb1
[sudo] password for kev: 
Mounting volume... Incomplete multi sector transfer detected in $MFT.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
Failed to startup volume: Input/output error.
FAILED
Attempting to correct errors... Incomplete multi sector transfer detected in $MFT.
ntfs_mft_load(): Failed.
Failed to load $MFT: Input/output error.
FAILED
Failed to startup volume: Input/output error.
Volume is corrupt. You should run chkdsk.
```

---

### Post by Gabt on 2009-03-29
> **Slim Odds said:**
> You don't get around much.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
Trying photrec now, seems to be extracting data, very messed up looking tho. Hopefully it rearranges them, eta 1h30

---

### Post by cool_fp on 2009-03-29
Thanks for sharing this problem here actually I am facing the same problem I have a lot data in my hard drive including the backups of all my site but when the same problem of light cut off I faced then after that when I restart that I can hear some noise in the hard disk as well so looking for a best solution please...........
_____________
[Resumes Templates]("http://checkmateresume.com")
[gochi juice]("http://cart.getgojionline.com")

---

### Post by Gabt on 2009-03-29
Still not found a solution to this, any other suggestions people!?

---

### Post by Gabt on 2009-03-30
:(

---

### Post by DigitalNoise on 2009-03-30
Ugh, honestly, having delt with NTFS partitions for years, I'm afraid that your best bet is to find someone with XP or Win2K or Vista who can hook your drive up and run some of Microsoft's recovery tools.

It sucks, and there are some Linux based tools out there that work with NTFS, but since MS developed it - I've just had better luck with their tools.

Though if your partition table got hosed during the power outage (which is what it sounds like), it may not be recoverable without low level work (ie. using a hex editor on the MBR/MFT), and I'm pretty sure that's beyond the scope of this forum.

If you know the maker of your HDD, you might try their support forums - sometimes they have tools available that can assist - couldn't hurt anyway.

---

### Post by hyper_ch on 2009-03-30
if you don't have any windows installed I wonder why you still use a ntfs partition... you might want to change that.

Another option would be to install a virtual WinXP for example in vmware or vbox and then add that partition as real drive to that virtual machine. That way you could troubleshoot it also.

---

### Post by DigitalNoise on 2009-03-30
> **hyper_ch said:**
> if you don't have any windows installed I wonder why you still use a ntfs partition... you might want to change that.
Yeah, I kinda wondered that myself, but if I had to guess I'd say it's probably left over from when the OP had Windows - since I'm pretty sure you can't change to another file system without wiping the drive, that might be why...
> **hyper_ch said:**
> Another option would be to install a virtual WinXP for example in vmware or vbox and then add that partition as real drive to that virtual machine. That way you could troubleshoot it also.
D'oh, I totally forgot about this - that could very well work.  I need to give that a shot the next time I need to troubleshoot an NTFS partition at work.

---

### Post by Gabt on 2009-03-31
> **hyper_ch said:**
> if you don't have any windows installed I wonder why you still use a ntfs partition... you might want to change that.

Another option would be to install a virtual WinXP for example in vmware or vbox and then add that partition as real drive to that virtual machine. That way you could troubleshoot it also.

I used to run windows, however, this disk is just a storage disk for me. I tended to change operating system randomly, from windows to linux, etc etc. Having the disk as NTFS allowed me to access the files from linux/windows.
Otherwise i wouldve just used ext2/3. Anyway, irrelevant.

Ive tried running a virtual windows XP with vbox and it couldnt read disk either, i think i have to accept my loss! :<

Cheers to everyone that tried.

---

### Post by hyper_ch on 2009-03-31
you can still try recovery software like photorec... maybe that can help.

---

