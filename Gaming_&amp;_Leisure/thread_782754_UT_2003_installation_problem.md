---
title: "UT 2003 installation problem"
date: 2008-05-05
forum: Gaming &amp; Leisure
---

### Post by NullZero1337 on 2008-05-05
Can you guys help me to install Unreal Tournament 2003 ?

My problem:

If I install UT2003 from the linux_installer.sh (on the 3rd disk), I get the following:
```
root@u2907:~# /media/cdrom0/linux_installer.sh
Copying to a temporary location...
Verifying archive integrity...tail: cannot open `+266' for reading: No such file or directory
Error in checksums: 454984593 is different from 738593104

```

I found this thread that fixed that could potentially fix the problem ([http://ubuntuforums.org/showthread.php?t=757104](http://ubuntuforums.org/showthread.php?t=757104)) but I cannot save/write to cdrom.

So I copied the file to my desktop, and edited it to fix the +266 problem, but now I'm getting the following :
```
root@u2907:~# /home/phil/Desktop/linux_installer.sh
Copying to a temporary location...
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2003 for GNU/Linux 2199....................................................................
This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
Fatal error, no tech support email configured in this setup
The setup program seems to have failed on x86_64/glibc-2.0

Fatal error, no tech support email configured in this setup
The program returned an error code (1)
```

Does anyone know how to fix this ?

Thanks!
Phil

---

### Post by Perfect Storm on 2008-05-05
That's a problem regarding newer version of linux(or should I say older game) that older games are point to an older release of glib.

I don't know if someone made newer version of the linux installer for UT2003.
Or try search google for the error, someone may have come with a solution to the problem.

---

### Post by NullZero1337 on 2008-05-05
Ok, I found a (newer?) installer, however, I am still getting a problem :

```

root@u2907:/home/phil/Desktop# ./utloki.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2003 2225beta3-multilanguage Update................................................................................................................................................................................................................................................................................................................................................................................................................................................
./update.sh: line 57: loki_patch: command not found

```

---

### Post by NullZero1337 on 2008-05-05
Sorry for the double:

I managed to around that by putting in ("utloki.run" is the installer):

```

cd /home/phil/Desktop 

linux32 sh utloki.run

```

Now it asks for installation path, but when I press enter it won't actually do it

```
Would you like to apply this update? [Y/n]: y

Please enter the installation path: []: /usr/local/games/ut2003
Please enter the installation path: [/usr/local/games/ut2003]: 
Please enter the installation path: [/usr/local/games/ut2003]: /root/.loki
Please enter the installation path: [/root/.loki]: /usr/local/games/ut2003
Please enter the installation path: [/usr/local/games/ut2003]: y
Please enter the installation path: [y]: this is
Please enter the installation path: [this is]: /usr/local/games/ut2003/
Please enter the installation path: [/usr/local/games/ut2003/]: 

```

Am I missing something here ?

Thanks!
Phil

---

### Post by Perfect Storm on 2008-05-05
you need to run it with admin permission **sudo**

sudo linux32 sh utloki.run


But don't start the game after, when installed exit the installer or you'll end up with permission problems.

---

### Post by NullZero1337 on 2008-05-05
> **Artificial Intelligence said:**
> you need to run it with admin permission **sudo**

sudo linux32 sh utloki.run


But don't start the game after, when installed exit the installer or you'll end up with permission problems.

Sorry, I forgot to tell you that I had already done "sudo -i"

Anyway, I still cannot get passed the installation path thingy even logged into root (>.<):

```
root@u2907:~# cd /root/Desktop
root@u2907:~/Desktop# sudo linux32 sh utloki.run
Verifying archive integrity... All good.
Uncompressing Unreal Tournament 2003 2225beta3-multilanguage Update................................................................................................................................................................................................................................................................................................................................................................................................................................................
=============================================================
Welcome to the Unreal Tournament 2003 2225beta3-multilanguage Update
=============================================================

Would you like to read the README for this update?  [Y/n]: y

		Unreal Tournament 2003: multilanguage Update 2225beta3
		      (http://www.unrealtournament.com/)

===============================================================

TECHNICAL SUPPORT
===================

	Website: http://liflg.org/
	Forum:   http://liflg.org/forum/

The Loki Installers for Linux Gamers Team


=============================================================
Would you like to apply this update? [Y/n]: y

Please enter the installation path: []: /usr/games/ut2003
Please enter the installation path: [/usr/games/ut2003]: 

```

Bah, I just learned that if you put /root/Desktop, it spews out a load of folders and readme's for patches, so methinks this loki thing doesn't actually install ut2003 in the first place :(

This is frustrating.

---

### Post by zxan on 2008-05-07
This worked for me!
```
sudo _POSIX2_VERSION=199209 linux32 sh ./linux_installer.sh
```

---

### Post by ernz on 2010-06-07
> **zxan said:**
> This worked for me!
```
sudo _POSIX2_VERSION=199209 linux32 sh ./linux_installer.sh
```

Thanks zxan! I can confirm this works for me on Ubuntu 10.04.

---

### Post by ernz on 2010-06-22
> **ernz said:**
> Thanks zxan! I can confirm this works for me on Ubuntu 10.04.

I spoke too soon - installation dialog doesn't respond to mouse clicks properly.

Bump.

---

### Post by T@. on 2011-04-28
> **zxan said:**
> This worked for me!
```
sudo _POSIX2_VERSION=199209 linux32 sh ./linux_installer.sh
```

Best comment on the web, thanks

---

