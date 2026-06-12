---
title: "wine segmentation fault"
date: 2006-01-10
forum: General Help
---

### Post by JacksonL on 2006-01-10
Hey guys. I installed wine (and *only* wine) a few days ago. I decided not to install winetools or winetk or xwine or any of that to help me out. All was going well an I managed to install warcraft 3 and almost have it running. The problem back then was that it wouldn't start at all with opengl and it wasn't playable in normal (directx, I'm assuming) mode. So I decided to upgrade my drivers using the HOWTO found on this forum and that all went well except now whenever I try to do *anything* in wine, including winecfg, it returns the single line "Segmentation Fault" like this:
```

jackson@jackson:~$ winecfg
Segmentation fault

```

soooo yeah. I have no idea how to fix this and I was wondering if anyone had any advice. thanks!

---

### Post by JacksonL on 2006-01-10
I hate to be a bother but I can't find a solution to this problem anywhere and I'd really appreciate some help.

---

### Post by dcstar on 2006-01-10
[QUOTE=JacksonL]I hate to be a bother but I can't find a solution to this problem anywhere and I'd really appreciate some help.[/QUOTE]
Rename your .wine directory and try again.

---

### Post by JacksonL on 2006-01-11
I tried renaming it and winecfging. I also tried renaming it, uninstalling it (complete removal in synaptic), reinstalling it. both of these produced the same error:
```

jackson@jackson:~$ winecfg
wine: creating configuration directory '/home/jackson/.wine'...
/usr/bin/wineprefixcreate: line 173:  6952 Segmentation fault      "${WINELOADER:-wine}" rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
wine: wineprefixcreate failed while creating '/home/jackson/.wine'.
jackson@jackson:~$ wineserver: could not save registry branch to /home/jackson/.wine-iAilvk/system.reg : No such file or directory
wineserver: could not save registry branch to /home/jackson/.wine-iAilvk/user.reg : No such file or directory

jackson@jackson:~$

```
any suggestions? thanks for the help so far :smile:

---

### Post by WIGGMPk on 2007-07-22
> **JacksonL said:**
> I tried renaming it and winecfging. I also tried renaming it, uninstalling it (complete removal in synaptic), reinstalling it. both of these produced the same error:
```

jackson@jackson:~$ winecfg
wine: creating configuration directory '/home/jackson/.wine'...
/usr/bin/wineprefixcreate: line 173:  6952 Segmentation fault      "${WINELOADER:-wine}" rundll32.exe setupapi.dll,InstallHinfSection DefaultInstall 128 wine.inf
wine: wineprefixcreate failed while creating '/home/jackson/.wine'.
jackson@jackson:~$ wineserver: could not save registry branch to /home/jackson/.wine-iAilvk/system.reg : No such file or directory
wineserver: could not save registry branch to /home/jackson/.wine-iAilvk/user.reg : No such file or directory

jackson@jackson:~$

```
any suggestions? thanks for the help so far :smile:

I had basically the same issure.

/home/jackson/.wine-iAilvk/system.reg

its trying to use ~/.wine-iAilvk/system.reg

instead of ~/.wine/system.reg..  I would try making a symbolic link to ~/.wine


Hope this helps

---

### Post by splintercellguy on 2007-07-22
I mighta missed something, but what version of Wine are you using?

---

