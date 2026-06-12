---
title: "Samba conky script"
date: 2009-01-07
forum: General Help
---

### Post by dollzii on 2009-01-07
Does anybody know if there is any way to monitor the size of samba shares in conky. 

I have a simple file server at home with a 1TB disk which is shared on my network in samba. Used by a vista machine and my ibex laptop. I would like to monitor how much diskspace thats left via conky...

Any clues?

---

### Post by dollzii on 2009-01-09
Bump

---

### Post by stepper on 2009-01-09
If its in fstab (locally mounted), then its the same way you check disk usage for a drive installed in your computer.

---

### Post by dollzii on 2009-01-11
Well, no, its not in fstab. I want to read the disk from my laptop, the disk itself is wired to my desktop/file server.

---

### Post by stepper on 2009-01-12
How do you access it on your Ibex laptop, if its not locally mounted?

---

### Post by dollzii on 2009-01-12
It's shared over the LAN. Samba

---

### Post by BoogeyOfTheMan on 2009-03-27
I am having the same issue.

I dont think its actually mounted, as the address to its location from this pc is:

smb://192.168.1.110/storage/

and not something like:

/media/disk-1

I wonder if thats why Opera and ktorrent wont let me save to that drive...

*EDIT*
I guess if I would have mounted it correctly it would have worked. Heres where I learned how.
[http://ubuntuforums.org/showthread.php?t=280473](http://ubuntuforums.org/showthread.php?t=280473)

---

### Post by fferral on 2011-07-30
This is far from a quick reply to the question of monitoring samba shares with Conky, but I will post it anyway in case someone is still looking at this problem. At least I'll post what worked for me:
# mkdir /media/nameofshare
$ sudo mount -t cifs -o username=yourusername,password=yourpassword //smbshare/nameofshare /media/nameofshare

---

### Post by fferral on 2011-07-30
:DThis is far from a quick reply to the question of monitoring samba shares with Conky, but I will post it anyway in case someone is still looking at this problem. At least I'll post what worked for me:
# mkdir /media/nameofshare
$ sudo mount -t cifs -o username=yourusername,password=yourpassword //smbshare/nameofshare /media/nameofshare

---

### Post by Morbius1 on 2011-07-30
From the looks of it it sounds like he mounted it through "Network" in Nautilus or perhaps "Connect to Server" in which case the remote share is automatically mounted at :

/home/user-name/.gvfs/share-name on server-name

---

