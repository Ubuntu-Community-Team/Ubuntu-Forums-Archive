---
title: "Transfering files ... how to...."
date: 2006-03-16
forum: Desktop Environments
---

### Post by cobbweb on 2006-03-16
Hi, 
  Is there any possible way for me to be able to transfer files from my Windows machine to my Linux machine? This could be a big problem if i cant get my files. Thanks, 

 Cobbweb

---

### Post by Sutekh on 2006-03-16
Are they on completely different machines?  Do you have network hardware available (router, switch, cables, etc)?

Do you plan to transfer files continuously between these machines or just every now and then?

---

### Post by Blairboy on 2006-03-16
If you need to transfer files to/from a windows machine (seperate hardware from your ubuntu box) then you need to install and configure samba.  It allows file sharing from linux to windows.  If you need to copy files from the same computer (as in dual boot) you just need to mount the windows partition.  A guide for mounting is available at ubuntuguide.org.  Hope this helps.

---

### Post by Jawbreaker4Fs on 2006-03-16
you could always run a local ftp server in windows using IIS, and then just access it through ubuntu using sftp or some gui ftp application...

---

### Post by cobbweb on 2006-03-16
[QUOTE=Blairboy]If you need to transfer files to/from a windows machine (seperate hardware from your ubuntu box) then you need to install and configure samba.  It allows file sharing from linux to windows.  If you need to copy files from the same computer (as in dual boot) you just need to mount the windows partition.  A guide for mounting is available at ubuntuguide.org.  Hope this helps.[/QUOTE]


 Ok I made a mount of my Windows Partion, but I cant seem to transfer files from my linux partion to my Windows Partion. How can i save things from my linux machine to my windows machine?

---

### Post by taurus on 2006-03-16
Are you using NTFS filesystem on your Windows system?  Better not write stuff to it from Ubuntu because you are asking for trouble with a capital T if you want to write to your NTFS from Linux...  If you want to write and read from both Ubuntu (or Linux) and XP, then create a partition with fat32 filesystem.  Then, both OSes would be happy to write and read from it without any problem.

---

### Post by cobbweb on 2006-03-16
[QUOTE=taurus]Are you using NTFS filesystem on your Windows system?  Better not write stuff to it from Ubuntu because you are asking for trouble with a capital T if you want to write to your NTFS from Linux...  If you want to write and read from both Ubuntu (or Linux) and XP, then create a partition with fat32 filesystem.  Then, both OSes would be happy to write and read from it without any problem.[/QUOTE]

OK, I found that your correct, I have an external hard drive and partioned it with fat32, works great on both systems.

---

