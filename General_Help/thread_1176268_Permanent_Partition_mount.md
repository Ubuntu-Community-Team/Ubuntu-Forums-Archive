---
title: "Permanent Partition mount"
date: 2009-06-02
forum: General Help
---

### Post by smartdude4ever on 2009-06-02
[LEFT]Hi Everyone!
I can mount my F drive using the following code:
sudo mkdir /media/MYDRIVE
sudo mount -t vfat /dev/sda7 /media/MYDRIVE
cd /media/MYDRIVE
ls

But I want to permanently mount the partition.
Is there anyway to do this?
Thanks!

[/LEFT]

---

### Post by MichaelSammels on 2009-06-02
Try installing the Storage Device Manager. Open Terminal and type:

```
sudo apt-get install pysdm
```
```
sudo pysdm
```

The bottom section runs the program.

---

### Post by ad_267 on 2009-06-02
Or you could do it the hard way:
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)

---

### Post by sahabcse on 2009-06-02
open the /etc/fstab and edit the following

/dev/sda7 /media/MYDRIVE ext3 defaults 0 0

For more info follow below url

[http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html](http://sahabm.blogspot.com/2009/03/mount-ntfs-fat32-windows-drive-in.html)

---

### Post by smartdude4ever on 2009-06-02
Thanks to Michael Sammels! That helped a lot! Pysdm is a nice program.............really appreciate your help!

---

### Post by MichaelSammels on 2009-06-02
No bother, glad I could have been of help.

As for the other posters, I thank them as well, I'd forgotten how to manually fstab things. :P

---

### Post by ad_267 on 2009-06-02
Hehe yeah sorry that wasn't really much help, thanks for pointing out pysdm.

---

### Post by MichaelSammels on 2009-06-02
To be honest, if we had a rep system, I'd rep you, because that is technically a faster way to do it, you just missed out:

```
sudo gedit /etc/fstab
```

:)

---

### Post by smartdude4ever on 2009-06-02
how do we do it? (fstab)

---

### Post by MichaelSammels on 2009-06-02
> **sahabcse said:**
> open the /etc/fstab and edit the following

/dev/sda7 /media/MYDRIVE ext3 defaults 0 0

you open /etc/fstab via:

```
sudo gedit /etc/fstab
```

---

### Post by ad_267 on 2009-06-02
pysdm is a tool for editing fstab, so you should be able to look in the fstab file and see the line created by pysdm.

---

