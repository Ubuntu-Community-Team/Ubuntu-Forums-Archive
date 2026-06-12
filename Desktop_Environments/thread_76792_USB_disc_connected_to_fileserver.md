---
title: "USB disc connected to fileserver"
date: 2005-10-15
forum: Desktop Environments
---

### Post by ManLord on 2005-10-15
I have a USB external HDD (NTFS) connected to my fileserver/webserver etc. (now referred to as PC2).

Here is the setup:
I have a computer with windows (PC1) that is connected to a router and so is PC2. I have set up Samba for PC2. So I can read/write to the shared resources (as my shared home dir). 

But when I try to share the /media/sdb6 (auto mount point for USB disc)  with Samba I can read it, but not write to it. Makes sense since I can't even write to NTFS from linux in the first place. The other partition of the USB disc is a FAT32 of 50 GB. I can write to this thought.

So my question is:
Is there a way to access(write to) the NTFS partition on the USB disc from windows over samba?
OR/AND
Can I have a 200 GB disc with FAT32?

---

### Post by joelito on 2005-10-15
This would sound strange to you but perhaps what you should do is to format as ext2/3 and get a windows ext2/3 driver...

If the file server is running linux you could just share the ext2/3 drive without doing anything to the windows pc, just make sure you know how to set the permisions for samba(wich I assume you do)

BTW - Have you considered using ftp in your local netwok ?

---

