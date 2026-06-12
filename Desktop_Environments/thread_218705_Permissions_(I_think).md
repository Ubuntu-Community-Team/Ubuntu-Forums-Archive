---
title: "Permissions (I think)"
date: 2006-07-18
forum: Desktop Environments
---

### Post by SonicSteve on 2006-07-18
Hi there,
I've been trying to gain access to a secured windows share on my XP machine.
To this point I've been able to mount the share permantently using fstab and samba. 
However for some reason even though in the fstab file the username and password to the share are specified I get only read access to it. If I use places/network servers and browse I then put in my username and password I get full access. 

also

I've noticed that many commands seem like CHmod and dmask contain a set of 3 #s.

so...
1. what are these #s and can someone point me at a resource that explains them.
2. Any ideas about the problem I described above?

---

### Post by OpsVentus on 2006-07-19
Did you specify read/write in your fstab? could well be only read is the standard for samba.

Cheers,
Bart.

---

### Post by philippe_carlo on 2006-07-19
Change the fstab line to look as follows:
```

//host/share  /mount/point  cifs  username=...,password=...,dmask=777,fmask=777,user 0 0

```

---

### Post by SonicSteve on 2006-07-19
Here is what finally worked,
I think its a bit open but... I'm the only one using this Ubuntu box, it's on a segmented lan behind a windows xp pro dhcp that's firewalled.

//server2/MP3files  /media/mp3files smbfs  username=*********,password=**********,umask=000, 0 0

I still don't know what dmask and fmask are but after searching around I found out that the #s are called a bitmask. I then found the umask option, and nothing of fmask or dmask. 

I found this site that was quite useful in figuring things out. Since Ubuntu is derived from debian most of the info is helpful.
[http://www.debianhelp.co.uk/general.htm](http://www.debianhelp.co.uk/general.htm) 

Thanks for everyone who helped

---

### Post by SonicSteve on 2006-07-19
I should say also that although I don't know what cifs stands for it was interchangeable with smbfs in the fstab line that mentioned above

---

