---
title: "smbpasswd file - where is it?!"
date: 2005-10-18
forum: Desktop Environments
---

### Post by DaveHartburn on 2005-10-18
Where is the smbpasswd file kept under 5.04? I've got samba up and running fine, but can't find the actual password file. Some documentation refers to /etc/samba/smbpasswd, but it is not there.

I've done a `find` for smbpasswd and 'private' (which I have also seen it called) and have found nothing. Even doing a find for files modified within the last 24 hours, did not turn up any thing obvious.

I have got pretty much the default samba configuration.

---

### Post by guy_uk on 2005-11-13
Hi

I'd love to know where this file is too!

Trying to configure the samba webmin module and its asking for this file...

I've googled and i appreciate where the file usually is, but its not there in hoary...

Please help us out

Guy

---

### Post by racecat on 2005-11-15
When I typed ```
bill@ubuntu1:~$ sudo find / -name smbpasswd -print
``` I got 
```
/usr/bin/smbpasswd
```

Hope it helps,

Bill

---

### Post by guy_uk on 2005-11-16
Thanks for the reply bill

sorry i should have explained better - the smbpasswd executable file is in /usr/bin but i would love to know where the actual password file is?

i may be wrong but i thought smbpasswd(the app) updates/configures the samba password file? 

Googling tells us where the file usually is, and what its usually called but the actual location of the file i don't know :( 

webmin needs it, otherwise i (or more specifically the people i want to give user-adding facilities to) can't add samba users...which kind of sucks when you want them to be able to create new users on the domain and stop calling me every day lol

thanks again, Guy

---

### Post by racecat on 2005-11-16
Oh, I feel silly. This forum seems to be very much off the beaten path since Breezy was released. Perhaps posting on the 5.10 forum may get the attention of one of the gurus. There's a good chance that it's in the same place in Hoary.

Good luck,
Bill

---

### Post by guy_uk on 2005-11-16
Don;t worry man

Good plan though, i just hope it is the same as in breezy!

Take care

Guy

---

