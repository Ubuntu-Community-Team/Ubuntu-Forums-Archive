---
title: "Unable to access ext4 partition"
date: 2009-05-07
forum: General Help
---

### Post by tdreyer1 on 2009-05-07
Installed a clean copy of jaunty x86. During the install, I chose the option to mount an ext4 partition to /media/share
Now that jaunty is installed, /media/share appears to be read only. When copying a file to it, I get the following error:
```
tdreyer1@tdreyer1-desktop:~$ cp /home/tdreyer1/Desktop/file /media/share/
cp: cannot create regular file `/media/share/file': Permission denied

```

The relevant portion of my fstab file:
```
...
# /media/share was on /dev/sda7 during installation
UUID=3dbe8eff-2a5c-4d01-ad87-8b45d6f61654 /media/share    ext4    relatime        0       2
...
```

I have tried changing "relatime" to "defaults" with no luck.
Any help on getting this partition to read/write?

---

### Post by tdreyer1 on 2009-05-08
Anyone?

---

### Post by taurus on 2009-05-08
If you want to write to /media/share without being root (or root privilege), then just change the ownership of /media/share from root to your login name, tdreyer1.

```
sudo chown -R tdreyer1:tdreyer1 /media/share
ls -la /media
```

---

### Post by tdreyer1 on 2009-05-08
Thanks! that worked great!

---

