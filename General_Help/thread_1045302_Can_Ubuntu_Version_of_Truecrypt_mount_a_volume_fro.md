---
title: "Can Ubuntu Version of Truecrypt mount a volume from an SMB Share?"
date: 2009-01-20
forum: General Help
---

### Post by Dysan911 on 2009-01-20
I have an XP Share at home that hosts a Truecrypt Volume.   All of my XP boxes can mount this volume using Truecrypt for XP.   I simply select the file and put in the network path.  

However on Ubuntu..  Instead of putting a network path I put in the SMB://networkpath and it click MOUNT.    It will prompt me for the Password.   Right after I type the correct PW it says..

No Such File or Directory
SMB://networkpath/blah/blah/blah.

What gives?

---

### Post by aaswt on 2009-02-14
I had the same problem on my Debian.

I finally managed to open volumes after mounting the shared folder :
```

mkdir /mnt/samba
mount -t smbfs \\\\192.168.1.10\\shared_folder /mnt/samba -o username=aaswt
```

In TrueCrypt, you can now open a volume using :
/mnt/samba/truecrypt_volume.dat

---

### Post by binbash on 2009-02-14
> **aaswt said:**
> I had the same problem on my Debian.

I finally managed to open volumes after mounting the shared folder :
```

mkdir /mnt/samba
mount -t smbfs \\\\192.168.1.10\\shared_folder /mnt/samba -o username=aaswt
```

In TrueCrypt, you can now open a volume using :
/mnt/samba/truecrypt_volume.dat

That helped me a lot!Thanks

---

### Post by Dysan911 on 2009-02-19
Wish I could say the same..    I get

Mount Error 111 = Connection refused
Refer to the mount.cifs(8) manual page etc etc.

Yet I can browse to the share with the Ubuntu GUI no problem.    :(

---

### Post by aaswt on 2009-02-20
Can we have a look to your smb.conf file, your /etc/hosts file, and what you put in the shell to mount the shared folder ?

---

