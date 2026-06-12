---
title: "permanently mounting network drives"
date: 2008-12-12
forum: General Help
---

### Post by ToddAndMargo on 2008-12-12
Hi All,

    I am running kubuntu (KDE 4.1) in a virtual window.  My
host is Cent OS 5.2.  The host has a SAMBA server which my
kunbunto guest can browse with Dolphin.

    Question, I would like these share to be permanently mounted
in my /mnt directory.  Can Dolphin do this?  Or, do I have to
write a start up script to do this?  Any suggestions?

Many thanks,
-T

---

### Post by HermanAB on 2008-12-12
Add an entry to /etc/fstab and it will be mounted when you reboot or issue 'mount -a'.  Read man fstab.

Cheers,

Herman

---

### Post by ToddAndMargo on 2008-12-12
I am not finding an example in the manual page, so I guessed.
It didn't work:

smb://server/CDs  /mnt/CDs smbfs user,noauto,exec    0       0

Can you correct my syntax?

Many thanks,
-T

---

### Post by ToddAndMargo on 2008-12-12
Figured out

1) mkdir /mnt/CDs; chmod -R 2777 /mnt/CDs

2)  # apt-get install smbfs

3)  added to fstab:

```
#//192.168.255.10/CDs /mnt/CDs smbfs credentials=/etc/samba/cred-file,uid=todd,gid=users 0 2

//192.168.255.10/CDs /mnt/CDs smbfs username=todd,password=iamnottellingyou,uid=todd,gid=users 0 2

```
Note: if you use credentials=/etc/samba/cred-file, the format is (no spaces!):
```

username=YourUsername
password=YourPassword
```

4) mount /mnt/CDs


Thank you for pointing me in the correct direction!

-T

---

