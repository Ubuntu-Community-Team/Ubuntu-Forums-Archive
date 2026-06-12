---
title: "pcsx2 setup problems"
date: 2009-01-11
forum: Gaming &amp; Leisure
---

### Post by Miles_Prower on 2009-01-11
So, I installed pcsx2 like this:
```
$ svn co https://pcsx2.svn.sourceforge.net/svnroot/pcsx2 pcsx2
```
That package is supposed to (and seems to) have all the plugins it needs to run.

The problem I'm hitting is that every time I try to run a game (file>>run cd), I get an error message: "Error opening GS plugin" I assume that using a different video plugin would fix this (currently using ZeroGS KOSMOS OpenGL 0.96.7), but I can't find one thats amd64 compatable. Anyone know where they can be found?


Also, I always use the location /media/cdrom0/ , since I have the disc in there. Is that wrong? Should I make an .Iso or something?

Thanks,
Taels

---

### Post by KingHanco on 2009-01-11
Why not contact them? [http://www.pcsx2.net/](http://www.pcsx2.net/)

---

### Post by hikaricore on 2009-01-11
Shoving users off to other sites without and additional information is not acceptable.

Please avoid it in the future.

---

### Post by Miles_Prower on 2009-01-11
The 64-bit graphics plugin was developed around Glew 0.4 , whereas the newest and most likely to be installed version is 0.5 . There is graphics plugin build around Glew0.5 , but it's returning an error:
```
Could not load GS plugin 'plugins//libZeroGSoglr.so.0.96.2': plugins//libZeroGSoglr.so.0.96.2: wrong ELF class: ELFCLASS32
```
This indicates that it's a 32-bit application. It seems like the most reasonable solution is to move back to Glew0.4, since I've never used it for anything but trying this emulator. 

wtf is glew, and how do I uninstall 0.5 and install 0.4?

I tried to find glew, but google failed me, and I couldn't track it down in the terminal, either:

```
taels@tornado:~$ which glew
taels@tornado:~$ which libglew
taels@tornado:~$ which glew-dev
taels@tornado:~$ which glew0.4
taels@tornado:~$ which glew0.5

```

---

