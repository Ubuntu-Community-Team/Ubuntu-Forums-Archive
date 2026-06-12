---
title: "How to Remove SAMBA password once and for all ?"
date: 2005-11-14
forum: Desktop Environments
---

### Post by edurm on 2005-11-14
Hello There,


After auto-monting my NTFS windows partition in fstab I would like to share it on my Windows workgroup.


The problem is that in one of my Windows network computer it keeps asking for login/pass to acess the Ubuntu shared files even after I change the smb.conf - How can I share my files whitout login/password ?


Here is my smb.conf 

;   security = share

[Linux]
path = /media/windows
available = yes
browseable = yes
public = yes
writable = no


1 - I already restarted samba
2 - I did everything as ubuntuguide.org
3 - I searched the forum and found nothing to solve it
4 - I'm using 5.10 - in 5.04 it worked :???: 

Thks'n advanced

---

### Post by paulvandenberg on 2005-11-14
Get rid of the semi-colon in front of *security = share* .

Paul

---

### Post by edurm on 2005-11-14
[QUOTE=paulvandenberg]Get rid of the semi-colon in front of *security = share* .

Paul[/QUOTE]


hum ... 	:wink:


I 'll try it tomorrow and I'll let you know if it woks, Thaks paul

---

### Post by edurm on 2005-11-15
That was it

Working fine now,


thank you again

---

### Post by andril on 2005-11-15
Thanks very much I can take this off my task list!  - stop the parade - it came right back on me :(

---

