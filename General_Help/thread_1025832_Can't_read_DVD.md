---
title: "Can't read DVD"
date: 2008-12-30
forum: General Help
---

### Post by Dinchamion on 2008-12-30
Hello,

I'm trying to install World of Warcraft on my linux box, but when I insert the WoTLK disc (I have a collectors edition, which is a DVD disc, appearantly with udf filesystem), I can't read it.

Here is what I get:

```
dinchamion@icarus:~$ wine /media/cdrom0/Installer.exe 
wine: could not load L"D:\\Installer.exe": Module not found
```

And here is what the contents look like, according to Ubuntu: [http://ubuntuforums.org/attachment.php?attachmentid=98119&stc=1&d=1230664808](http://ubuntuforums.org/attachment.php?attachmentid=98119&stc=1&d=1230664808)

My /etc/fstab:

```
proc            /proc           proc    defaults        0       0
UUID=cb36b017-3ac6-434f-816d-e62e6787244f /               ext3    relatime,errors=remount-ro 0       1
UUID=f5c5d6c7-973f-4f2e-9fb3-718fbeedfbc0 /home           ext3    relatime        0       2
UUID=4959-D65E  /media/shared   vfat    utf8,umask=007,gid=46 0       1
UUID=6cffaa44-9818-497b-844d-91aaf41923e6 none            swap    sw              0       0
/dev/sr0       /media/cdrom0   auto user,auto,exec,rw,utf8 0       0
```

I have udftools installed too. Any ideas?

---

### Post by amauk on 2008-12-30
If I remember correctly, the Wrath of the Lich King disc uses hidden files
(god knows why)

you have to edit your /etc/fstab and enable the viewing of hidden files on a CD

Open up a terminal, and enter:
```
sudo gedit /etc/fstab
```

Edit the file as below
(these are my entries, edit to suit

**Before**
```
/dev/scd0       /media/cdrom0   udf,iso9660 user,noauto,exec,utf8 0       0
```
**After**
```
/dev/scd0       /media/cdrom0   udf,iso9660 **unhide**,user,noauto,exec,utf8 0       0
```

---

### Post by Dinchamion on 2008-12-31
Yep, that solved it, and I could copy over the files to my hard drive! Thanks!

---

