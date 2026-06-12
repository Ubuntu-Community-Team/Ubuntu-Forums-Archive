---
title: "Ubuntu Jaunty question!"
date: 2009-08-04
forum: Gaming &amp; Leisure
---

### Post by xFlowx on 2009-08-04
This question is no longer needed. Thanks for the help, Winter Weaver.

---

### Post by WinterWeaver on 2009-08-04
try installing it through PlayOnLinux. [URL="http://www.playonlinux.com/en/"]http://www.playonlinux.com/en/
[/URL]
They have custom wine scripts that helps you to install specific apps and games. This worked for me a while back.
That said... GuildWars is one of the few games, that really struggle in linux. It's almost always a issue to get it working nicely in Ubuntu. (wel for me anyway)

---

### Post by xFlowx on 2009-08-04
**EDIT: I lied. It installed correctly, and now I'm trying to get it set up so I can try it! Thank you!**

> **WinterWeaver said:**
> try installing it through PlayOnLinux. [URL="http://www.playonlinux.com/en/"]http://www.playonlinux.com/en/
[/URL]
They have custom wine scripts that helps you to install specific apps and games. This worked for me a while back.
That said... GuildWars is one of the few games, that really struggle in linux. It's almost always a issue to get it working nicely in Ubuntu. (wel for me anyway)

I've installed this before, and it keeps giving me weird ...messages? I suppose that's what it is. For example, it spit this out when I tried to install it:
```

flow@ubuntu:~$ sudo wget http://deb.playonlinux.com/playonlinux_jaunty.list -O /etc/apt/sources.list.d/playonlinux.list
--2009-08-04 13:53:42--  http://deb.playonlinux.com/playonlinux_jaunty.list
Resolving deb.playonlinux.com... 91.121.5.64
Connecting to deb.playonlinux.com|91.121.5.64|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 44 [text/plain]
Saving to: `/etc/apt/sources.list.d/playonlinux.list'

100%[======================================>] 44          --.-K/s   in 0s      

2009-08-04 13:53:42 (2.55 MB/s) - `/etc/apt/sources.list.d/playonlinux.list' saved [44/44]

flow@ubuntu:~$ sudo apt-get update
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the list directory
flow@ubuntu:~$ sudo apt-get install playonlinux
```Any ideas? It seems as though it doesn't want to work. That might be me, though.

---

### Post by Grishka on 2009-08-04
this is all very odd. GW is one of the few windows mmorpgs that works flawlessly for me without doing anything special. it installs fine, runs fine, the only problem I have is with some graphical glitches. maybe you haven't installed your video drivers? what is your graphics card?
on a side note, READ THE DAMN STICKIES!!!! there's a separate subforum for questions about windows-related stuff. this should be moved.

---

### Post by xFlowx on 2009-08-04
I'm just getting rid of this thread now, probably giving up on this forum place 8D

---

