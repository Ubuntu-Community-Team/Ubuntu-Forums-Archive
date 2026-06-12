---
title: "Get files off hardrive"
date: 2009-01-16
forum: General Help
---

### Post by jv13613 on 2009-01-16
Hi,
  I have a windows machine I want to get files by ubuntu live cd so I know how to do it when windows crashs. I have windows xp pro. In the ubuntu live cd 8.10 my hard drive comes up. When I drill down into Documents and settings\my user name all the folders are there. But when i go into my documents folder there are no files there except desktop.ini and some folders. Even these folders are empty except desktop.ini. I know I have files in this folder. I can access these files in windows but not in ubuntu. please help. I have a usb drive to put the files on.

---

### Post by taurus on 2009-01-16
Is the partition/drive formatted as ntfs filesystem?  How do you mount it?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
df -h
```

---

### Post by Herman on 2009-01-16
Hmmm, that's an unusual problem, if there are files there, Ubuntu can normally 'see' them.
I don't know for sure, but maybe try running a file system check, (CHKDSK /R), from the [Windows XP Recovery Console]("http://www.kellys-korner-xp.com/win_xp_rec.htm") your Windows XP Professional Installation CD.

Maybe, if you're lucky, that might even fix your Windows problem for you too, and you might not even need to rescue your files.

Regards, Herman :)

---

### Post by ajgreeny on 2009-01-16
Have you actually got a problem at the moment or are you just making sure you can solve one if it should occur?  Whichever it is, have a look in all the other users in Documents and settings as I seem to recall that when I used a windows box last my files were spread all over the place.  I certainly find the linux file system much more intuitive now I know my way around it.

---

### Post by jv13613 on 2009-01-16
My system has not crashed YET. I mount using ntfs-3g. it is the only hard drive and partion in my computer. and my file system is fine no errors.

---

### Post by Bucky Ball on 2009-01-16
Are you intending to install Ubuntu or just use it from Live CD for the purpose of emergency data retrieval? If the latter, maybe Ubuntu Live CD is not the premium option ...

---

### Post by jv13613 on 2009-01-16
yes i just want to use ubuntu live cd for emergengy data retrevail. I do not want to install ubuntu on this computer.

---

