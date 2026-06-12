---
title: "[SOLVED] World of Padman uninstall"
date: 2008-08-24
forum: Gaming &amp; Leisure
---

### Post by L337_K3y5 on 2008-08-24
I did the installation wrong on World of Padman for Linux, and I need to unistall it.  It installed it to usr/games.  I installed it by an executable text file.  I got it from [http://worldofpadman.com]("http://worldofpadman.com").  I need I guess to install the 32 bit libraries as well to make it run as I get this error:  ```
andrew@andrew-laptop:~$ wop
./wop-engine.i386: error while loading shared libraries: libvorbisfile.so.3: cannot open shared object file: No such file or directory
andrew@andrew-laptop:~$ 

```  I haven't the slightest idea how to do it.  Sorry to do this fast, but I'm getting off, I'll check back tomorrow.:)

---

### Post by Perfect Storm on 2008-08-25
Well, no need to launch i386 as there's one for 64-bit, here's a guide: [http://gaming.gwos.org/doku.php/guides:64bit:wop](http://gaming.gwos.org/doku.php/guides:64bit:wop)

I don't quite how you installed it, but uninstall it manually;

check usr/games and delete the wop folder

```
cd usr/games
ls -a
sudo rm -rf <wop folder>
```

There's properly a bin file of wop in /usr/bin it needs deletion as well. Further more there's a WOP in your directory (it's hidden), .wop

---

