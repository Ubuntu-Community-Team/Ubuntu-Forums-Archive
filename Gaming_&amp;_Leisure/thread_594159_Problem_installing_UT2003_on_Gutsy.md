---
title: "Problem installing UT2003 on Gutsy"
date: 2007-10-27
forum: Gaming &amp; Leisure
---

### Post by BOZG on 2007-10-27
I'm having problems installing UT2003 on Gutsy.  I can run the installer with no problems but as soon as I try to enter an installation path, the Begin Installation box greys out and locks.  Does anyone know any ways of getting around this?


This is the code in the terminal when I run the installer:
```
stephen@stephen-desktop:~$ cd /cdrom
stephen@stephen-desktop:/cdrom$ sh linux_installer.sh
Copying to a temporary location...
Verifying archive integrity...tail: Warning: "+number" syntax is deprecated, please use "-n +number"
An embedded MD5 sum of the archive exists but no md5sum program was found in /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." /tmp/makeself7176 -check
 All good.
Uncompressing Unreal Tournament 2003 for GNU/Linux 2107tail: Warning: "+number" syntax is deprecated, please use "-n +number"
......................................................................


```

---

### Post by Morokiane on 2007-10-28
I just install to 

/home/user/games/ut2k3

/home/user/

and it works fine.  However when it asks for my cd key it hangs and won't except it.

---

### Post by BOZG on 2007-10-28
My Begin Installation button stops working.  As soon as I enter a path, it locks up and won't let me install.  Someone else on #ubuntu on IRC had the same issue.

---

### Post by Crafty Kisses on 2007-10-28
> **Morokiane said:**
> I just install to 

/home/user/games/ut2k3

/home/user/

and it works fine.  However when it asks for my cd key it hangs and won't except it.

My friend has had the same problem, he fixed it though, I'll ask him.

---

### Post by arizonagroovejet on 2007-10-28
> **Morokiane said:**
> 
 However when it asks for my cd key it hangs and won't except it.

[http://ubuntuforums.org/showthread.php?t=592752&highlight=2003](http://ubuntuforums.org/showthread.php?t=592752&highlight=2003)

---

### Post by arizonagroovejet on 2007-10-28
> **BOZG said:**
> My Begin Installation button stops working.  As soon as I enter a path, it locks up and won't let me install.  Someone else on #ubuntu on IRC had the same issue.

Maybe you're specifying an install directory you do not have write permissions for? I notice in your first post you are not using running the installer under sudo. If you want to install to anywhere other than your own home directory you need to run the installer under sudo.

```
stephen@stephen-desktop:/cdrom$ sudo ./linux_installer.sh
```

---

### Post by BOZG on 2007-10-28
I'll test that out now but I don't think it will solve it.  It locks as soon as I type / and when I delete it, it remains locked.

---

### Post by BOZG on 2007-10-28
No, doesn't work with sudo and still locking.  I did notice that in the installer itself, it tells me to respond to the license dialog as soon as I try to enter a path though there's no license dialog window or mention of it in the terminal.

---

### Post by Morokiane on 2007-10-28
> **arizonagroovejet said:**
> [http://ubuntuforums.org/showthread.php?t=592752&highlight=2003](http://ubuntuforums.org/showthread.php?t=592752&highlight=2003)

Well that fixed that...now I'm getting crashes like Unreal Tournament where it doesn't want to run...console says...

```
fcntl: Operation not permitted
fcntl: Operation not permitted

OpenGL renderer relies on DXTC/S3TC support.

History: 

Exiting due to error

```

Hope all this helps out Boz when he finally gets his installed...haha.

---

### Post by BOZG on 2007-10-29
Stealing my thread!

---

