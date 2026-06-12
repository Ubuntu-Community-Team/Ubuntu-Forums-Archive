---
title: "Samba troubles, root taking ownership?"
date: 2006-07-13
forum: Desktop Environments
---

### Post by tyraen on 2006-07-13
This is probably a stupid question/something stupid I'm doing.

I have a Windows Samba share that I can connect to fine, permissions are all set up correctly, but the problem is on the Linux side.  I created a folder in my home directory that I want as the mount location, so I do:
sudo mount -t smbfs //ip/share -o username=user,password=pass

And at this point root takes ownership of the mount point, and I can't copy files to it or anything.  I unmounted, sudo chowned it back to myself, but when I mount it again root takes ownership.  I can't mount it without sudo, so what should I be doing differently?

Thanks.

---

### Post by Ramses de Norre on 2006-07-13
I don't know much about samba mounting but you could try adding an option (so after the -o flag) ```
umask=0000
``` which should set a umask so that everyone has full permissions, you can change this permissions to some more save values when it works. But test it first because I don't know whether samba shares support this option or not.

---

### Post by MikeBenza on 2006-07-13
Open your smb.conf (/etc/samba/smb.conf) and go to the share you want to have ownership of.

Add the param *force user = YourUserName*

i.e.:
```

[global]
	workgroup = BENZA
	netbios name = SERV
	os level = 40
	ldap ssl = no

[mike]
	path = /home/mike
	username = mike
	valid users = mike
	force user = mike
	force group = wheel
	read only = No

```

I'm fairly sure that'll do the trick.

---

### Post by tyraen on 2006-07-13
Hmm, that didn't do it, but I tried uid=username as an option and that added me to the permissions for the directory.  Yay.  Thanks for the hint!

---

### Post by tyraen on 2006-07-13
The share is on the XP box though, I'm looking to mount it from the Linux system.  I haven't changed anything in the smb.conf file yet, do I need to?

---

### Post by Ramses de Norre on 2006-07-13
Didn't you say it was solved? If not did you try my suggestion? And the uid option didn't work neither? If everything works you don't have to edit the smb.conf.

---

### Post by tyraen on 2006-07-13
Yes, it works when I added the uid to it.  I just wondered if I was even going at it from the right direction. :)

Thanks for your help!

---

### Post by Ramses de Norre on 2006-07-13
You certainly were;)

---

