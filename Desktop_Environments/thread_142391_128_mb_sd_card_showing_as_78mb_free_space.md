---
title: "128 mb sd card showing as 78mb free space"
date: 2006-03-10
forum: Desktop Environments
---

### Post by ade234uk on 2006-03-10
OK got a weird problem. I have been playing around with my new 20 in 1 card reader and 128mb sd card in Ubuntu. I am really chuffed that is has detected this first time. 

I decided to put some files on the sd card and then delete them. I made sure that the hidden files was checked. 

However after deleting the files It says that I only have 78mb of free space. Something on this card is pinching space how do I format or ensure everything is throughly deleted in on this card.

---

### Post by kaamos on 2006-03-10
Open a terminal and go to the mount point (like "cd /media/usbdisk") and check the output of "ls -la". This should show if there is something still hiding on the card.

---

### Post by linuxishard on 2006-03-10
If you open that folder through root you might see a folder named trash-(username)- Delete it...!!!
sorry if it doesnt work but i had that problem

---

### Post by ade234uk on 2006-03-10
How do I open this folder through root?

I have accessed things via root throught the command line, but never a folder.

---

### Post by kaamos on 2006-03-10
Opening as root has no difference for what folders/files are showing. Normal user and pressing ctrl+h should be enough. As the command posted above.

---

### Post by ade234uk on 2006-03-10
I went to cd /media/usbdisk and entered ls -la in the terminal and it came back with the following

adrian@ubuntu:/media/usbdisk$ ls -la
total 20
drwx------  2 adrian adrian 16384 2006-03-10 16:06 .
drwxr-xr-x  9 root   root    4096 2006-03-10 16:05 ..

I still dont know what is knicking the space.

---

### Post by Ramses de Norre on 2006-03-10
It says there are two directories on it with 20 files in total. One owned by you the other by root.
Didn't it included the folder names? Should be behind the file stamp.
If so: sudo rm -r "directoryname" will delete them.

---

### Post by ade234uk on 2006-03-11
Thank you I will try this when I get home and see if it frees up the space.

---

