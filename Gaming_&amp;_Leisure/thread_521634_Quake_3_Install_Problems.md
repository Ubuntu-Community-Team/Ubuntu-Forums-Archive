---
title: "Quake 3 Install Problems"
date: 2007-08-09
forum: Gaming &amp; Leisure
---

### Post by DonMatlock on 2007-08-09
Hi all,
Iam currently using Ubuntu ver 7.04, I am having issues starting the insaller for Quake 3 Linux...the error is as follows:

server@server-desktop:~$ su -
Password: 
root@server-desktop:~# cd /media/cdrom0/
root@server-desktop:/media/cdrom0# ks
-su: ks: command not found
root@server-desktop:/media/cdrom0# ls
autorun.inf  bin   icon.bmp  quake3.sh  setup.data  win32
baseq3       Help  icon.xpm  README     setup.sh
root@server-desktop:/media/cdrom0# sh setup.sh
setup.sh: 9: function: not found
x86
root@server-desktop:/media/cdrom0# ./setup.sh
-su: ./setup.sh: /bin/sh: bad interpreter: Permission denied
root@server-desktop:/media/cdrom0# 

I have tried sh setup.sh and./setup.sh and continueto get an error...am Imissing thecorrect command?

Any help is much appreciated

Don

---

### Post by dropwire on 2007-08-09
Hey Don you can find a how-to from ID software here:

[http://zerowing.idsoftware.com/linux/q3a/INSTALL](http://zerowing.idsoftware.com/linux/q3a/INSTALL)

Hope that helps you out

---

### Post by dmn_clown on 2007-08-09
[download 1.32c]("http://planetquake.gamespy.com/View.php?view=Quake3.Detail&id=2212")
```

:$ mkdir -p quake3/baseq3
mount /dev/hdc
cp /media/cdrom/Setup/baseq3/*.pk3 quake3/baseq3/
unzip quake3-1.32c-linux.zip
cd quake3
./quake3.i386

```

---

