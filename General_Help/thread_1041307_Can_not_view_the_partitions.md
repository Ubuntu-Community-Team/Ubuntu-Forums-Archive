---
title: "Can not view the partitions"
date: 2009-01-16
forum: General Help
---

### Post by sushil.katre on 2009-01-16
Hi,

I don't have any experience with Linux. Today I installed Ubuntu and had a first hand experience with Linux, after some struggle I got connected to my Access Point and I am typing this query from Ubuntu :P

Please pardon me for the lack of knowledge and working experience with linux.

While installing Ubuntu, I partitioned my 80 GB hard disk, 1st with 15Gb with mount point as /

2nd partition with 30 GB with mount point as /SK

3rd partition with 34 GB with mount point as /Sushil

Now, when I go to Places>Computer I expected to see three DRIVES.

While I see only one which is Filesystem. Under filesystem I see two folders with name SK and Sushil

under these folders I see a folder named lost+found with an emblem stating unreadable.

Is this normal?

Is there a way to view three Disk under Places>Computer?

Any pointers will be appreciated.

Thanks.

-> Sushil

---

### Post by taurus on 2009-01-16
Maybe you want to remount those two partitions to /media/SK & /media/Sushil in /etc/fstab.

---

### Post by john183 on 2009-01-16
Yes seeing those drive as folders /SK and /Sushil. In linux when you mount an internal harddrive as /* (where * is any name you choose) it ends up in the filesystem the way you are seeing your files. Only drives that are mounted in /media/* (star here is just like above) will show as separate drives as far as i know.

---

### Post by sushil.katre on 2009-01-16
Hi Taurus,

Thanks for the suggestion but it doesn't make any sense to me, I am completely new to this.

I'll appreciate if you can brief me more on this.

-> Sushil

---

### Post by sushil.katre on 2009-01-16
Aaah Tautus/Johnathan, now it makes sense to me. Can you guide me as to how I make these changes now. Do I hold a chance now or you get this option only during installation.

-> Sushil

---

### Post by redilyn on 2009-01-16
I think you need to change your mount points. The setup you have is mounting them in the root (/) folder.

Try the following, it should help

```

sudo mkdir /media/SK
sudo mkdir /media/Sushil

```

Next you need to change the entries in fstab. I am going to assume you used ext3

```

sudo gedit /etc/fstab

```

Add/Change the following
```

From

UUID=8cc4c096-0491-4c82-9feb-9162f15cbe08 [COLOR="Red"]/SK [/COLOR] ext3    relatime        0       2

To

UUID=8cc4c096-0491-4c82-9feb-9162f15cbe08 [COLOR="Red"]/media/SK[/COLOR]  ext3    relatime        0       2


From

UUID=8cc4c096-0491-4c82-9feb-9162f15cbe08 [COLOR="Red"]/Sushil [/COLOR]          ext3    relatime        0       2

To
UUID=8cc4c096-0491-4c82-9feb-9162f15cbe08 [COLOR="Red"]/media/Sushil [/COLOR]          ext3    relatime        0       2

```

I hope this is somewhat clear. I can help if you have problems.

---

### Post by taurus on 2009-01-16
From a terminal, Applications -> Accessories -> Terminal, edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and replace /SK with /media/SK and /Sushil with /media/Sushil.  Save the changes and close down gedit editing window.  Now, you need to create those two new mount points.

```
sudo mkdir /media/SK /media/Sushil
```
Reboot and those two partitions are now mounted to /media/SK & /media/Sushil.  

And since they are ext3 filesystem, you can change the ownership of those two mount points from root to your login name so you can write to them anytime you want without using sudo/gksudo.

Assuming your login name is sushil, run

```
sudo chown -R sushil:sushil /media/SK
sudo chown -R sushil:sushil /media/Sushil
ls -la /media
```

---

### Post by Carl Hamlin on 2009-01-16
> **sushil.katre said:**
> Now, when I go to Places>Computer I expected to see three DRIVES.

-----BEGIN PGP SIGNED MESSAGE-----
Hash: RIPEMD160

Doesn't work that way under Linux. Your partitions will mount as part of a homogenous filesystem, where you have specified that they mount. They will never come up as separate drives - your expectation that they should is consistent with a user switching from Windows, but is in error in this instance.

-----BEGIN PGP SIGNATURE-----
Version: GnuPG v1.4.9 (GNU/Linux)

iEYEAREDAAYFAklw1wsACgkQyLm4ydrABvdf7wCg36t/SfdKLYsUz9GirE0jY/wK
T+YAoOl52SDfbZr0Xe1ctRNpCMXc0Pbp
=T77w
-----END PGP SIGNATURE-----

---

### Post by redilyn on 2009-01-16
Actually what they are expecting is exactly what will happen if they follow the directions above....

Atleast it will look that way

---

### Post by sushil.katre on 2009-01-16
Guys, its working perfectly fine. Appreciate your help.

Thanks a lot. 

Hope to have more fun with Ubuntu!!!!

-> Sushil

---

