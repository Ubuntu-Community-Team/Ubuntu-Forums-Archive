---
title: "Mount .img file"
date: 2006-03-23
forum: Desktop Environments
---

### Post by web-man on 2006-03-23
Hi
how can i virtualy open a .img file?
Its a dvd-video and i want to watch in pc

---

### Post by akiro.yamamoto on 2006-03-23
I'm not 100% sure you can do this directly...
However :
Install loop, then create a temp directory, then.
```

sudo mkdir /media/temp (your new temp mount point)
mount -t udf your_file.img /media/temp -o loop (the meat of the operation)

```

Your .img file should now be available under /media/temp just like a normal dvd.
The reason you use udf here instead of iso9660 is because udf is normally associated
with DVD while iso is normally associated with CDs..

I hope this info helps ;)

---

### Post by web-man on 2006-03-23
Tnks :)
But...
root@ubuntu:/home/martinho# mount -t udf 123.img /media/temp -o loop
mount: wrong fs type, bad option, bad superblock on /dev/loop0,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

---

### Post by engla on 2006-03-23
I have a dvd image named name.img.. I just open it with vlc, and it plays fine, so try that with vlc or another media player of choice.

---

### Post by taurus on 2006-03-23
I believe mplayer can handle both .bin and .img besides all those usual suspects like avi, mpg, wmv, etc.

---

### Post by stoeptegel on 2006-03-23
Depends.
A "track-at-onces" *nrg image can be mounted with loop like a *iso file, but (for what i've seen) a "disc"at-one" created file can't. But frankly i have no idea howto determine the nrg file is either disc-at-one or track-at-once.

---

### Post by skroops on 2007-12-01
just download the "iat" package, then run it from the command-line on the file to convert all those types of files into standard iso images.

---

### Post by didier on 2007-12-02
mount .BIN, .MDF, .IMG and .NRG
FUSE module to mount ISO filesystem images

 Homepage: [http://fuse.sourceforge.net/wiki/index.php/FuseIso](http://fuse.sourceforge.net/wiki/index.php/FuseIso)

---

### Post by stoeptegel on 2008-01-28
For anyone reading this and still need the info; there is now [acetoneiso2](http://www.kde-apps.org/content/show.php/Acetoneiso2?content=71954) and it works great.

---

### Post by Belak on 2008-04-09
> **skroops said:**
> just download the "iat" package, then run it from the command-line on the file to convert all those types of files into standard iso images.
This is extermely useful. I'e been looking for something like this.

---

### Post by chiques on 2008-05-23
You guys rock!

---

