---
title: "x86 to AMD64 upgrade"
date: 2009-02-08
forum: General Help
---

### Post by bitplane on 2009-02-08
some while ago, i downloaded and installed xubuntu 8.10 x86 on my p4. some shorter while ago, i got myself an AMD64 dual core and installed windoze to discover how badly multithreaded most games still are ;)

after a while, i got bored with these games, it clearly was time to do some serious work, so i tried downloading xubuntu 8.10 again, but since my usb wireless stick is terribly unstable it wouldn't work really.. i remembered having this 8.10 CD laying around and installed it.

then i lived happily ever after, until i remembered having an AMD64 machine and the x86 xubuntu installed. ever since, i've wondered wether it'd be any faster with the AMD64 version..

i could have skipped typing the above and just ask the 4 questions all this implied:

1. should the AMD64 version be faster on an, err, AMD64? (it should, right?)
2. does the AMD64 version have any disadvantage over the x86 version? (i remember the 64bit winXP being quirky, there might be a link here)
3. what exactly is the difference anyway? is it only the kernel, or must there be different packages/binaries too? if so, are these 64bit version available for all ubuntu supported packages?
4. how does one upgrade, if possible at all, from the x86 version to the AMD64 version?

excuse my possible linguistic errors, for i am dutch ;)

tnx in advance!

---

### Post by oldos2er on 2009-02-08
You would need to do a fresh install of 64-bit. There are 64-bit versions of most everything in the repositories.

 I've been running 64-bit Ubuntu for well over a year; there are no disadvantages I can see.

---

### Post by jespdj on 2009-02-08
See the stickies in the [x86 64-bit users forum](http://ubuntuforums.org/forumdisplay.php?f=343).

One of the main advantages of 64-bit is that you can use more than 4 GB memory. Another advantage is that especially processor-intensive programs run faster (because of technical reasons, read [x86-64 on Wikipedia](http://en.wikipedia.org/wiki/X86-64) for details).

64-bit Ubuntu does not have the same kind of issues as 64-bit Windows. The problem with 64-bit Windows is that many hardware manufacturers still don't make 64-bit drivers. On Ubuntu, almost everything is open source, so there are 64-bit versions of almost all software available (and also proprietary 64-bit drivers from nVidia and ATI). Besides that, 32-bit software also runs on 64-bit Ubuntu, but it might be a little harder to install. The only 32-bit programs you might want to use are some proprietary programs such as Google Earth and Skype. Installing those is easy via [Medibuntu](http://medibuntu.org/), it contains packages to install those 32-bit programs on 64-bit Ubuntu easily.

---

