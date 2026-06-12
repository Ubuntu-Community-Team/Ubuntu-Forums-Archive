---
title: "Problems installing Diablo 2"
date: 2005-08-23
forum: Gaming &amp; Leisure
---

### Post by xodeus on 2005-08-23
Hi guys.
I've problems installing Diablo 2.
I've mounted the Iso and try to run the installer but it is not found. Here's it.
```
mariusz@networkadmin101c:~$ sudo mount Spil/Diablo_II/Diablo_CD1.iso /media/iso -t iso9660 -o loop
mariusz@networkadmin101c:~$ wine /media/iso/INSTALL.EXE
wine: cannot find '/media/iso/INSTALL.EXE'
mariusz@networkadmin101c:~$
``` 

Here's my #mount
```
mariusz@networkadmin101c:~$ mount
/dev/sda1 on / type ext3 (rw,errors=remount-ro)
proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /dev/shm type tmpfs (rw)
usbfs on /proc/bus/usb type usbfs (rw)
/dev on /.dev type unknown (rw,bind)
none on /dev type tmpfs (rw,size=5M,mode=0755)
none on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/home/mariusz/Spil/Diablo_II/Diablo_CD1.iso on /media/iso type iso9660 (rw,loop=/dev/loop0)
mariusz@networkadmin101c:~$
``` 

There you can see that the file is mounted properly but something is very wrong.
It installs fine on my windows but not here.

Please help

---

### Post by doclivingston on 2005-08-23
Can you do a `ls /media/iso` to see what it is showing as being on the CD?

---

### Post by xodeus on 2005-08-23
[QUOTE=doclivingston]Can you do a `ls /media/iso` to see what it is showing as being on the CD?[/QUOTE]
 Here is it
```

mariusz@networkadmin101c:~$ ls -A /media/iso
AUTORUN.INF  D2DATA.MPQ    D2SPEECH.MPQ  DSETUP16.DLL  EXTRAS       SETUP.MPQ
BINKW32.DLL  D2README.HTM  DIABLOII.ICO  DSETUP32.DLL  INSTALL.EXE  SUPPORT
crack        D2SFX.MPQ     DIRECTX7      DSETUP.DLL    SETUP.EXE
mariusz@networkadmin101c:~$

```

---

### Post by Mishura on 2005-08-23
I think I know why.

Edit your wine's config file (~/.wine/config).

Add a Drive (Lets say, X:) and have the mount point "/".  For example:

```
[Drive X]
"Path" = "/"
"Type" = "hd"
"Label" = "root"
"Filesystem" = "win95"
```

This will allow wine to see your entire HDD system.  So, if /media/iso is where you mounted your ISO file, the DOS equivalent is:

X:\media\iso

Try it and it should work.  If not, then I don't know...

---

### Post by xodeus on 2005-08-25
[QUOTE=Mishura]I think I know why.

Edit your wine's config file (~/.wine/config).

Add a Drive (Lets say, X:) and have the mount point "/".  For example:

```
[Drive X]
"Path" = "/"
"Type" = "hd"
"Label" = "root"
"Filesystem" = "win95"
```

This will allow wine to see your entire HDD system.  So, if /media/iso is where you mounted your ISO file, the DOS equivalent is:

X:\media\iso

Try it and it should work.  If not, then I don't know...[/QUOTE]
 Sorry. It still wont load.
```

mariusz@networkadmin101c:~$ cd Spil/Diablo_II/
mariusz@networkadmin101c:~/Spil/Diablo_II$ ls
Diablo_CD1.iso  Diablo_CD2.iso  Diablo_CD3.iso
mariusz@networkadmin101c:~/Spil/Diablo_II$ sudo mount Diablo_CD1.iso /media/iso -t iso9660 -o loop
Password:
mariusz@networkadmin101c:~/Spil/Diablo_II$ wine /media/iso/INSTALL.EXE
wine: cannot find '/media/iso/INSTALL.EXE'
mariusz@networkadmin101c:~/Spil/Diablo_II$

```

---

### Post by KrazyPenguin on 2005-08-30
Open the folder and click on Install.exe

Choose to open with WINE if it doesn't do it automatically.

See if that helps.

---

### Post by cooldood82 on 2009-02-16
> **KrazyPenguin said:**
> Open the folder and click on Install.exe

Choose to open with WINE if it doesn't do it automatically.

See if that helps.

I do that but it starts loading for about 15 or 20 seconds and then eventually quits and nothing happens?

what am i doing wrong?

---

### Post by cbbnewbie on 2010-06-21
hello,, i have the same problem what it says when i click and open it with wine  is "insert install disk"

---

### Post by dim3000 on 2010-06-21
> **cbbnewbie said:**
> hello,, i have the same problem what it says when i click and open it with wine  is "insert install disk"

You do realize you awoke a 5 year old thread?

Anyways go here: [http://appdb.winehq.org/appview.php?iVersionId=49](http://appdb.winehq.org/appview.php?iVersionId=49)

And read the HOW-TO, it should be self-explanatory.

---

### Post by hikaricore on 2010-06-21
epic fail

---

### Post by overdrank on 2010-06-21
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]

---

