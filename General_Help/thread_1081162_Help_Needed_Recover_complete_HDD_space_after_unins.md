---
title: "Help Needed: Recover complete HDD space after uninstall"
date: 2009-02-26
forum: General Help
---

### Post by shivbrahmi on 2009-02-26
Hello, Apologize if this is a repeat of a previously solved issue but I checked everything before posting.

Background:

I wanted to do a complete unistall of Ubuntu 8.04 from an external 250 gb USB Seagate HDD and install ubuntu 6.06

Issue:

- Install of new system gives error
- further noticed that the drive reads as *_229 GB_* instead of the actual *_250.1 GB_* that Ubuntu 8.04 was able to recognize at the time of first install, this is also true when the drive is mounted under windows XP
- Only during the install process of 8.04 doe sthe drive register 250.1 GB of space *_(tried re-installing 8.04 again)_* but does not allow any other OS to be installed or read the drive space correctly
- *Tried with the open suse 11.1 install cd and it does not register the complete drive space as well, as  if it does not at all exist, registers as 229 GB only*  then gives a error indicating something regarding permissions and that it cannot go on with the install

Please help me wipe out this drive completely and recover the complete 250 GB space

Thanks
Shiv

---

### Post by DagMan on 2009-02-26
[http://hardforum.com/showthread.php?t=1347640](http://hardforum.com/showthread.php?t=1347640)

[http://www.epowermac.com.au/Shop/pc/viewContent.asp?idpage=28](http://www.epowermac.com.au/Shop/pc/viewContent.asp?idpage=28)

You have a few megabyte discrepancy, which could be a swap file.

---

### Post by Lars Stokholm on 2009-02-26
> **shivbrahmi said:**
> Install of new system gives errorWhat does it say?

> **shivbrahmi said:**
> Please help me wipe out this drive completely and recover the complete 250 GB spaceYou do know that a drive labeled 250GB (G = 1000³) hasn't got more than 232GiB (Gi = 1024³) of space on it, right? 250 / 1.024³ = 232,83. That said and for the record, you can wipe out a drive completely with the dd command. Assuming you're drive is accessible from a Live CD:```
dd if=/dev/zero of=/dev/yourdrive
```

---

### Post by shivbrahmi on 2009-02-26
Thank you Lars and Dagman , really appreciate your help .. guess was just being illiterate .. Dagman it was a swap file .. Thank you both once again.

Regards,
Shiv

---

