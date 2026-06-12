---
title: "copy large files to external drive, viewed by linux and windows?"
date: 2009-05-07
forum: General Help
---

### Post by mrose1120 on 2009-05-07
Is there a way to copy large files (some over 4GB) to an external 400GB drive, so that both Linux and Windows XP/2003 could have access to them?  I have a test VMWare environment running in Ubuntu 8.10 server and I want to put the backups on an external drive that I could transfer between a windows or linux system if necessary.  It seems Fat32 can't have files greater than 4GB

Thanks!

---

### Post by kanikilu on 2009-05-07
NTFS is pretty much your only option here, unless you want to install some flakey drivers on Windows...

---

### Post by ddrichardson on 2009-05-07
Linux has had NTFS support for quite a while.

---

### Post by mrose1120 on 2009-05-07
you can do an NTFS file system that Linux can write to and so can Windows? For some reason I didn't think that could happen, how would I do that?

---

### Post by ddrichardson on 2009-05-07
Without much effort, I'm writing to a NTFS external USB drive now from Ubuntu and haven't done anything.

---

### Post by mrose1120 on 2009-05-07
cool,

I see documentation on doing it using gparted, but i'm not using a gui, do you know of instructions to install it from fdisk?

---

### Post by mrose1120 on 2009-05-07
nevermind  think i got it

---

### Post by binbash on 2009-05-07
I am using external ntfs HDD to store BIG mkv videos.You can access them with ubuntu and windows without any problems.

---

