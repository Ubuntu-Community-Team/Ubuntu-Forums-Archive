---
title: "Samba username prompt"
date: 2006-09-27
forum: Desktop Environments
---

### Post by Jason_Hampson on 2006-09-27
I'm quite new to this, so please be gentel...

I have a desktop pc I've dual booted Dapper with Windows MCE 2005. The pc has two hard drives, a smaller one that I've pationed (NTFS & EX3). I also have a second larger hard drive (fat32), which I want to share over my network.

I've edited the /etc/samba/smb.conf file to add the following two entries:

[public]
  comment = Public Folder
  path = /home/public
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

[music]
  comment = Music Folder
  path = /media/hdb1/Music
  public = yes
  writable = yes
  create mask = 0777
  directory mask = 0777
  force user = nobody
  force group = nogroup

The first entry points to the local EX3 partion, the second to a folder on the fat32 drive.

From my Windows machine I can see both of the folders. I can access the public folder (on the EX3 partion), but when I try to open the fat32 folder I get a username and password prompt box. The username field is locked to <server-name>\Guest i.e. linux-desktop\Guest

I've tried my sudo password, but to no avail.

Any suggestions please......

---

### Post by hardhatamoeba on 2006-09-30
you need to add a user on the samba side, 

t this point you should be able to see the samba server from any windows system in the same workgroup but you won't be able to access the share; not until you add the user(s).

Samba authenticates its users through its local database. Once you have saved the changes to smb.conf , you need to add the users.

Since you enabled the encrypted password option in your smb.conf, you need to add the users with encrypted password.

Add your existing users to samba or create new users and then add them to samba.

[root@server2 samba]# smbpasswd –a agustin
	New SMB password: ********
	Retype new SMB password:********

Enter the password in 8 character length or more, if you enabled the user name length specification, then it must meet the requirement. Note that agustin is an existing user in the system. 

i hope that helps

---

### Post by djRobbieF on 2006-09-30
alternatively, you could allow samba to share to guest users.  It's not secure, but if you're only sharing with a lan, it might be fine.

ie.

```
read only = yes
guest ok = yes
use client driver = yes
```

---

### Post by djRobbieF on 2006-09-30
HERE is an INSECURE way:

sudo /etc/samba/smb.conf

Go down to the line that says:
; security = user

Change it to say:
security = share

Restart samba (/etc/init.d/samba restart)

Again, this opens up your fileshares to ANYONE on your network, so if that's ok, this is fine.

---

### Post by Jason_Hampson on 2006-10-01
Still no luck. 

Its only a small personal LAN so i'm not worried about an authenticated logon.

My config file now looks like:

[global]
  workgroup = MSHOME
  security = share


[public]
  comment = Public Folder
  path = /home/public
  read only = no
  guest ok = yes
  use client driver = yes

[music]
  comment = Music Folder
  path = /media/hdb1/Music
  read only = no
  guest ok = yes
  use client driver = yes

I can access the /home/public directory, but I'm prompted for a password on the /media/hdb1/Music folder. The setting are identical, so I'm not sure what the cause is. I though it may be the it's on a second fat32 drive and not the primary one?

I've used ls -l on the folder to check the access and this was the result:

drwxrwx--- 93 root plugdev     32768 2006-09-25 16:16 Music

Which I though was ok?

Thanks

---

### Post by Jason_Hampson on 2006-10-01
Actually, I can see that folder is missing permssions that the other one has:

   drwxrwxrwx  4 root   root   4096 2006-09-28 15:20 public


I tried to change the permssion using:

   sudo chmod a+rw Music

but they still look the same:
   
   drwxrwx--- 93 root plugdev     32768 2006-09-25 16:16 Music

---

### Post by Jason_Hampson on 2006-10-02
Problem has now been sorted.

If anyone has similar trouble then mine was due to a access permission problem. 

I needed to change fstab so all users had at least read access.

---

