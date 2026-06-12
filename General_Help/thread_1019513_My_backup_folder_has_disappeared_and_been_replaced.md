---
title: "My backup folder has disappeared and been replaced with random file!"
date: 2008-12-23
forum: General Help
---

### Post by B3Nji on 2008-12-23
Hi,

I would really appreciate help with this. 
I have backed up my important files to an external USB IDE hard drive. Now when I come to put my files back I find that the folder is gone, but there is a file with the same name as my folder. When I look at the folder in list view it tells me the type of the file is "pipe"? 

In the backup is all my photos of my friends and family, more importantly  holidays away with my girlfriend (she wont like the fact I lost all those pics!), I would hate to have lost them all! 

Thank you again. 
Ben

---

### Post by Titan8990 on 2008-12-23
What did you use to backup and what command? Also, if its the only copy that you have, its not really a backup.

---

### Post by B3Nji on 2008-12-23
> **Titan8990 said:**
> What did you use to backup and what command? Also, if its the only copy that you have, its not really a backup.

I just copied and pasted the folder from my PC over to my external hard drive. I didnt use a command, was all done with nautilus. I could browse the folder on my external fine. Just when I came to copy it back it was gone :( btw, i did make a point of properly ejecting the drive so i wouldn't loose anything.

I was putting it on my external drive because I wanted to install my system a fresh. I understand it wasn't a backup because I was removing the original. 

Can you help?

---

### Post by Titan8990 on 2008-12-23
I'm not sure exactly what kind of copy nautilus does. There is a possibility that is a -L copy which would not work properly on a NTFS drive.


The best I can offer is to tell you how to search for a file name that you know existed in the backup. If its not there, its gone:


find /path/to/backup/drive -name 'nameoffile'


In the future, use rsync to make your backups as it is very reliable.

---

### Post by Seq on 2008-12-23
I've had luck in the past using photorec to recover files from usb flash drives as well as hard disks.

The most important thing is to _**stop using the disk**_. Seriously, you want to stop it from mounting automatically and ensure you only mount it read-only, if at all -- photorec works on the device itself, so it does not need to be mounted.

---

### Post by B3Nji on 2008-12-23
> **Seq said:**
> I've had luck in the past using photorec to recover files from usb flash drives as well as hard disks.

The most important thing is to _**stop using the disk**_. Seriously, you want to stop it from mounting automatically and ensure you only mount it read-only, if at all -- photorec works on the device itself, so it does not need to be mounted.

OK thanks for all your input. 

I have tried using 'photorec' but it does not detect the disk so its a no go there. 

Titan8990 when I do the find command do I have to give it the exact file name? Or can I use a word I think is in one of the files? 

Cheers.

---

### Post by Titan8990 on 2008-12-23
If you don't want it to be exact then do this:


find /path/ -name '*FILE*'


use an aterisk on each end of the name so that it will find things that "contain" what you put in and not just exact matches.

---

### Post by B3Nji on 2008-12-23
> **Titan8990 said:**
> If you don't want it to be exact then do this:


find /path/ -name '*FILE*'


use an aterisk on each end of the name so that it will find things that "contain" what you put in and not just exact matches.

OK thanks for your help. 

No luck with that, cant find any of the files. They must be in the 'pipe' file i mentioned, have no idea if I can get them out of there though.

---

### Post by Titan8990 on 2008-12-23
What is referring to it as a pipe file?


What is the name of the file?

---

