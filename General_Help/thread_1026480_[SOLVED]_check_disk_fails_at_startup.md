---
title: "[SOLVED] check disk fails at startup"
date: 2008-12-31
forum: General Help
---

### Post by chriskin on 2008-12-31
when starting the computer, checking an ext3 partition fails everytime asking me to enter maintenance shell or type control-d .
it also tells me that a log will be written in /var/log/fsck/checkfs 
when i read it , this is what was in it :

Log of fsck -C -R -A -a 
Wed Dec 31 14:10:14 2008

fsck 1.41.3 (12-Oct-2008)
fsck.ext3: Unable to resolve 'UUID=bc73e46e-9e27-4cf3-92be-114e20791617' 
fsck died with exit status 8

Wed Dec 31 14:10:14 2008

the problem started happening after i tried formatting the partition to ntfs with gparted live cd


what i need to do is either fix it or just make the computer not check it at startup, i do not have a big problem to not having ubuntu recognise it, it is just a 10gb partition

---

### Post by drs305 on 2008-12-31
This is normally the result of fsck trying to run a check on a device listed in fstab whose UUID has changed. If you update the fstab entry the error will be eliminated.

To check your UUIDs:
```

sudo blkid

```

To edit your fstab (substitute your text editor for gedit if different):
```

sudo cp /etc/fstab /etc/fstab.bak
gksudo gedit /etc/fstab

```

---

### Post by chriskin on 2008-12-31
it is fixed :)

THANK YOU :)

---

