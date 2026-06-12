---
title: "Formating volume has lost+found and denies copy access"
date: 2009-04-12
forum: General Help
---

### Post by Flywaver on 2009-04-12
Greetings,

I formated a volume as EXT3 in order to use it for media files such as images and MP3's. But everytime I format the volume, I open it and there's a lost+found folder that is denied access, and I can't cope any files to this volume as it denies me the access! :(

Btw, I formated this partition with GParted, tried several times and no success!

How do I completely format this partition so that I can get total access to it?

BTW, I tried sudo nautilus and delete the lost+found folder and then copy my mp3 files to the volume...but when I restarted there was still the lost+found folder and no MP3!

Thanks in advance!

Cheers!

---

### Post by taurus on 2009-04-12
If you want to write to that new drive/partition without being root (sudo), then you need to change the ownership of the mount point for that partition/drive from root to your login name.

_Assuming_ your login name is flywaver and the mount point for that partition/drive is /media/sdb1, you could so something like

```
sudo chown -R flywaver:flywaver /media/sdb1
ls -la /media
```

---

### Post by drs305 on 2009-04-12
The lost+found folder is a folder produced when system checks are run (fsck). Rather than delete errors it finds, it places the bits into the lost+found folder for your review. If you delete it the next time fsck runs on that partition it will be recreated.

---

### Post by Flywaver on 2009-04-12
Thanks guys,

Everything runs perfect...gotta love dumping windows forever!! :)

Cheers!

---

### Post by Flywaver on 2009-04-12
Hmmm...I can't create a folder within that volume now! 

Seems that I could only delete the lost+found folder and copy my MP3's after doing these lines of code: 

```
sudo chown -R flywaver:flywaver /media/sdb1
ls -la /media
```

Do I have to reboot before gaining complete access?

Cheers!

---

### Post by taurus on 2009-04-12
Is the mount point /media/sdb1?

```
mkdir /media/sdb1/testing
ls -la /media/sdb1
```

---

### Post by Flywaver on 2009-04-12
> **taurus said:**
> Is the mount point /media/sdb1?

```
mkdir /media/sdb1/testing
ls -la /media/sdb1
```

No...I used the example yo gave me...I redid the code for my proper volume and it now works...weird!

Thanks again!

---

