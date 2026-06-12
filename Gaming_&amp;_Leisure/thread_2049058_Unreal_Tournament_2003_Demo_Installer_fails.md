---
title: "Unreal Tournament 2003 Demo Installer fails"
date: 2012-08-27
forum: Gaming &amp; Leisure
---

### Post by dboot on 2012-08-27
Hello! I'm trying to set up a demo server for some friends. Any help would be appreciated!

I downloaded the Unreal Tournament 2003 Demo from here: [http://www.fileplanet.com/112996/110000/fileinfo/Unreal-Tournament-2003-Demo-v2206-(Linux)](http://www.fileplanet.com/112996/110000/fileinfo/Unreal-Tournament-2003-Demo-v2206-(Linux)).
```

utplayer@utserver:~# uname -a
Linux utserver 3.2.0-29-generic-pae #46-Ubuntu SMP Fri Jul 27 17:25:43 UTC 2012 i686 i686 i386 GNU/Linux
utplayer@utserver:~# cat /etc/lsb-release
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.1 LTS"
```

I ran into this problem and solution: [http://ubuntuforums.org/showthread.php?t=757104](http://ubuntuforums.org/showthread.php?t=757104).

```
utplayer@utserver:~$ ./ut2003demo_lnx-2206.sh.bin
Verifying archive integrity...tail: cannot open `+266' for reading: No such file or directory
Error in checksums: 3529085597 is different from 764522044
utplayer@utserver:~$ export _POSIX2_VERSION=199209
```

Now I'm getting this error:
```

utplayer@utserver:~$ ./ut2003demo_lnx-2206.sh.bin
Verifying archive integrity...An embedded MD5 sum of the archive exists but no md5sum program was found in /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
If you have md5sum on your system, you should try :
env GUESS_MD5_PATH="FirstDirectory:SecondDirectory:..." ./ut2003demo_lnx-2206.sh.bin -check
 All good.
Uncompressing Unreal Tournament 2003 for GNU/Linux Demo 2206...
Second stage unpacker running...
Starting actual installer...
The setup program seems to have failed on x86/unknown

Fatal error, no tech support email configured in this setup
The program returned an error code (1)

```

Thanks!

---

### Post by R33D3M33R on 2012-08-28
The package coreutils should have md5sum utility included.

---

### Post by dboot on 2012-08-28
Already at the latest version:

```
utplayer@utserver:~# apt-get install coreutils
Reading package lists... Done
Building dependency tree
Reading state information... Done
coreutils is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.

```

Even though there's an md5sum error, I don't think that's the cause of the install failure. Thanks!

---

### Post by dboot on 2012-10-01
Here's hoping...

::bump::

---

