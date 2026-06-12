---
title: "mounting network drive"
date: 2006-06-20
forum: Desktop Environments
---

### Post by xolot1 on 2006-06-20
my dad has a large hard drive connected to our home network.  it is detected easily by ubuntu (no setup, etc), and i can access files seamlessly.  ive put a bunch of music on this harddrive, and now i was hoping id be able to add it to my amarok connection.

under Places->Network Servers->[harddrive] i can right click on the icon and 'make link.'  this puts an icon on my desktop, and says thats its mounted.  if this is so, where is its mount point? or perhaps it is not mounted as my internal harddrive is?

anyways, how can i scan this collection of music with amarok?

(i realize i havent included much info about the drive, what is needed?  the icon says 'smb' on it, properties says its location is "smb://mshome/x-desktop "  [mshome is the network])

thanks

---

### Post by Ctrl+Alt+Del on 2006-06-20
the smb:// location is a gnome only thing. amarok, beeing a kde app is not able to recognize it.
In order to get access to it you will have to mount it properly.
sudo nano -w /etc/fstab
add a line similar to this
//hostname/share             /mnt/mountpoint         smbfs   credentials=/etc/samba/passwords,fmask=0777,dmask=0777,user

in /etc/samba create a file called passwords and enter the following details:
username=yourusername
password=yourpassword

after that you should be able to mount it using 'mount /mnt/mountpoint'
It will be automounted every time you reboot.

---

### Post by xolot1 on 2006-06-20
thanks for the reply.
im not doing something correct, and hopefully you can see what it is:

my fstab entry looks like this
```
//mshome/DSM-G600/HDD_a/share     /drive    smbfs   credentials=/etc/samba/passwords,fmask=0777,dmask=0777,user
```

mshome is the workgroup thing
dsm-g600 is the drive itself
HDD_a is the folder i am interested in
/drive is the mount point

/etc/samba/passwords looks like
```

username=willi
password=[my sudo password]

```

im getting a mount error, and dmesg | tail gives the following:
[CODE]
smbfs: mount_data version 1684370019 is not supported
[CODE]

help?
thanks

---

### Post by disturbed1 on 2006-06-20
[http://ubuntuforums.org/showpost.php?p=1160100&postcount=5]("http://ubuntuforums.org/showpost.php?p=1160100&postcount=5")

Samba is old, CIFS includes many improvements over mounting SMB shares.

The username and password are the **WINDOWS** username and password, not Ubuntu's ;)

---

### Post by Ctrl+Alt+Del on 2006-06-21
try
```
//DSM-G600/HDD_a     /drive    smbfs   credentials=/etc/samba/passwords,fmask=0777,dmask=0777,user
```
as disturbed1 noted, cifs should work too

---

### Post by manutremo on 2006-06-21
For my DSM-G600 it works without credentials:

//g600/HDD_a    /media/g600/a   smbfs   dmask=777,umask=777     0       0

---

### Post by xolot1 on 2006-06-21
**cifs** returns:
```

CIFS VFS: cifs_mount failed w/return code = -22

```
[B]

//g600/HDD_a /drive smbfs dmask=777,umask=777 0 0[/B]
or   **//dsm-g600/HDD_a /drive smbfs dmask=777,umask=777 0 0**
or **//DSM-G600/HDD_a /drive smbfs dmask=777,umask=777 0 0**

returns:
```

smbfs: mount_data version 1935764836 is not supported

```

which is a different error then before.:confused:
should this imply i somehow have the address wrong?

---

### Post by Ctrl+Alt+Del on 2006-06-22
No idea what these errors mean:
Just to check:
The Box is named DSM-G600?
The Share is named HDD_a?
the mountpoint /drive exists?
trying to mount as root gives the same error?

---

### Post by d0w on 2006-09-17
Trying to mount a smbfs, i got this message, too:

> smbfs: mount_data version 1935764836 is not supported

I solved installing the smbfs package

```
sudo apt-get install smbfs
```

Good luck.

PD: I see it's been a while since somebody said something but i got hung with it so I hope it helps somebody.

---

