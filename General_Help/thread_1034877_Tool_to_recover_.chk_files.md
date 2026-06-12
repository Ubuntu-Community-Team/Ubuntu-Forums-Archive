---
title: "Tool to recover .chk files?"
date: 2009-01-09
forum: General Help
---

### Post by ToshibaLaptoplinux on 2009-01-09
Is there any native Linux tool that recovers windows .chk files?


I made the complete switch to Linux and occasionally encounter minor bumps such as this. I would really like to AVOID having to go to a Win box to deal with this so any suggestion feedback would be greatly appreciated.

---

### Post by cajunlibra on 2011-01-07
I'd like to do this as well. I remember running a command that scanned the folder and renamed the files to the appropriate extension. Unfortunately, I cannot remember what that command was.

How can I recover all of these files again?

Thanks

ubuntu 10.10 on Dell Precision M20

---

### Post by psusi on 2011-01-07
file will try to identify what kind of file it is, then you can try renaming it to use the appropriate extension.

---

### Post by hawkmage on 2011-01-07
Using the "file" command on the individual chk files can help determine what they are but one of the issues you will have is that the the chk files are likely fragments of files and not entire files.

---

### Post by Garthhh on 2011-01-08
I'm having a similar problem
I've converted a few old pc's to mint & 10.04 for my extended family
I'm working on my sister in laws old pentium 4 
she would like to recover some of the data off the hdd
she believes there are emails that were backed up by outlook
of course she can't remember the password
I was able to copy the entire contents of the hdd over to a different one that's running 10.10
the directories are labeled found.001, to found.031, each one containing a few files labled
/home/***/Documents/54AA-C26C/FOUND.007/FILE0000.CHK
there's 15g supposedly

---

### Post by cajunlibra on 2011-01-09
Can anyone advise how to avoid this problem from occurring in the future?

---

### Post by psusi on 2011-01-09
> **cajunlibra said:**
> Can anyone advise how to avoid this problem from occurring in the future?

Don't use a FAT filesystem.

---

### Post by cajunlibra on 2011-01-17
What would be the most appropriate file system to use for this partition shared between both Ubuntu and XP?

---

### Post by Garthhh on 2011-01-17
I use ntfs on an external hard drive to store my music, works fine on either 
I use Grsync to transfer large files, though I'm not sure what is equivalent is for XP, probably unison

---

### Post by psusi on 2011-01-18
> **cajunlibra said:**
> What would be the most appropriate file system to use for this partition shared between both Ubuntu and XP?

The only other choice that Windows supports, and prefers: NTFS.

---

