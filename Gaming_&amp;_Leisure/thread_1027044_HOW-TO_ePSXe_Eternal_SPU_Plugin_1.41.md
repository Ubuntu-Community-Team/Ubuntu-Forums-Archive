---
title: "HOW-TO: ePSXe Eternal SPU Plugin 1.41"
date: 2008-12-31
forum: Gaming &amp; Leisure
---

### Post by Ioky on 2008-12-31
The reason why the Eternal SPU Plugin 1.41 are causing all the problem is that the "libstdc++2.10-glibc2.2" package is is no long available since ubuntu 8.04. However, it come with ubuntu 7.10. So simply go to ubuntu package search, then download and install the package manually, will do. 

After that my Eternal SPU Plugin is now working. and it is the best sound plugin. (I think)

I don't know why this package is no long available, it might because problem? it might because conflict? it might because out of date. and is no long needed. well I don't know, but it is sure needed with few software out there. As it is not official supported, use your as your own risk. 

All I can tell you is that it work for me, and it is only available with x86 not x86_64.

here is the link of the package.
[http://packages.ubuntu.com/gutsy/libstdc++2.10-glibc2.2](http://packages.ubuntu.com/gutsy/libstdc++2.10-glibc2.2) 

If anyone know how to make it work on 64bit system, please share your HOW-TO,

---

### Post by Wisp558 on 2009-12-02
Oooh, I think I may know this one.

I run my 32bit ePSXe in my x64 linux by cheating a little.
(This is on karmic, btw)

I took the required (old) 32bit .debs, (not necessarily karmic, i used jaunty gtk1.2 libs) and used dpkg -x on them. Then I just copied the libraries into the main epsxe directory. Then, I ran epsxe with a script that sets LD_LIBRARY_PATH to epsxe's directory. and wahlah! It all works. I got the dpkg -x bit from [link]("http://newyork.ubuntuforums.org/showthread.php?t=1300476").

The idea is that you can do this for the missing eternal SPU libraries as well, although I have never tried it.

This works for me, but for some reason, it won't let me run any plugin but the softX one by Pete. THis is a major bummer, as my GeForce 8500 GT is definitely capable of the XGL2 plugin... But when I put the library in the plugins directory, epsxe segfaults on trying to open the video configuration tab. Same with the Mesa plugin. idk if this is specific to my setup, but I thought I should mention it in case others find my issues. 

Sorry for necro-ing, but I wanted to pop out that suggestion.

---

### Post by Perfect Storm on 2009-12-03
Quite okay as long you came up with a suggestion to solve the problem. And the issue(s) is still relevant today.


Why not use getlibs for the task? Much easier.

---

