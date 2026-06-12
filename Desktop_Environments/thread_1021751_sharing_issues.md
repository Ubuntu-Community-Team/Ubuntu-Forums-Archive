---
title: "sharing issues"
date: 2008-12-25
forum: Desktop Environments
---

### Post by num on 2008-12-25
i am trying to share a folder between a linux computer and a windows computer. i installed samba on the linux part but i get this login screen whenever i try to see what the computer has sharing on the windows side. i do not see the shared folder that i selected on the linux side.

image:

[IMG]http://i44.tinypic.com/oqejau.jpg[/IMG]

---

### Post by albinootje on 2008-12-25
> **num said:**
> i am trying to share a folder between a linux computer and a windows computer. i installed samba on the linux part but i get this login screen whenever i try to see what the computer has sharing on the windows side. i do not see the shared folder that i selected on the linux side.

Can you post the share-parts of your /etc/samba/smb.conf ?

And do get errors when you try this command on the Linux-box 
(no password required for this command, just hit <enter> when asks) :
```

testparm
smbclient -L localhost

```
You might have to install smbclient if you haven't done that yet.

---

### Post by num on 2008-12-25
should there be an enter in the code:

```
testparm
smbclient -L localhost
```


?

---

### Post by albinootje on 2008-12-25
> **num said:**
> should there be an enter in the code:

```
testparm
smbclient -L localhost
```


?
Yes, those are two separate commands.

---

### Post by num on 2008-12-26
this is what i get:

```
administrator@server:~$ testparm
Load smb config files from /etc/samba/smb.conf
Processing section "[printers]"
Processing section "[print$]"
Loaded services file OK.
Server role: ROLE_STANDALONE
Press enter to see a dump of your service definitions

[global]
	server string = %h server (Samba, Ubuntu)
	map to guest = Bad User
	obey pam restrictions = Yes
	passdb backend = tdbsam
	pam password change = Yes
	passwd program = /usr/bin/passwd %u
	passwd chat = *Enter\snew\s*\spassword:* %n\n *Retype\snew\s*\spassword:* %n\n *password\supdated\ssuccessfully* .
	unix password sync = Yes
	syslog = 0
	log file = /var/log/samba/log.%m
	max log size = 1000
	dns proxy = No
	usershare allow guests = Yes
	panic action = /usr/share/samba/panic-action %d

[printers]
	comment = All Printers
	path = /var/spool/samba
	create mask = 0700
	printable = Yes
	browseable = No

[print$]
	comment = Printer Drivers
	path = /var/lib/samba/printers
administrator@server:~$ 

```

---

### Post by albinootje on 2008-12-26
Okay, you didn't defina a share, here's an example of two shares, which you can put before or after the printer section you already have :

```

[test1]
   comment = test1
   path = /home/samba/test1
   public = yes  
   writable = yes
   printable = no
   create mode = 0775   
   directory mask = 0775
[test2]
   comment = test2
   path = /home/samba/test2
   valid users = adrian
   public = yes
   writable = yes
   printable = no
   create mode = 0775
   directory mask = 0775

```

"test1" is a public share, and "test2" is only meant for samba-user adrian.

After adding your share(s) accordingly, you restart samba :
```

/etc/init.d/samba restart

```
And test again on your Windows-box

---

### Post by num on 2008-12-26
ok how do i add shares using the gui?

i got a folder called "share" in the home folder. I want to share that folder, how i do this?

---

### Post by albinootje on 2008-12-26
> **num said:**
> ok how do i add shares using the gui?

i got a folder called "share" in the home folder. I want to share that folder, how i do this?

Right-click on that folder, click on "Sharing Options", and select your options.

If you don't want a guest/public share, then you will need to create a samba-user (see : man smbpasswd).

---

### Post by num on 2008-12-26
i did that though for that folder "share". i dont understand, i did select those options. Do I need to restart the system?

---

### Post by albinootje on 2008-12-26
> **num said:**
> i did that though for that folder "share". i dont understand, i did select those options. Do I need to restart the system?

Is your "workgroup" name the same ?

If you're using the workgroup "HOME" in XP, and you're using workgroup "WORKGROUP" in /etc/samba/smb.conf it won't work.

Check this line in /etc/samba/smb.conf :
```

workgroup =

```
After changing it, restart samba :
```

sudo /etc/init.d/samba restart

```

---

