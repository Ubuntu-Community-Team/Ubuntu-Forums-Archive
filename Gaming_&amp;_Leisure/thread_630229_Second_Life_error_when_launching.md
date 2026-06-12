---
title: "Second Life error when launching"
date: 2007-12-03
forum: Gaming &amp; Leisure
---

### Post by Jabb3r on 2007-12-03
./secondlife: line 87:  4540 Segmentation fault      (core dumped) LD_LIBRARY_PATH="`pwd`"/lib:"`pwd`"/app_settings/mozilla-runtime-linux-i686:"${LD_LIBRARY_PATH}" $LL_WRAPPER bin/do-not-directly-run-secondlife-bin -settings settings_releasecandidate.xml -channel "Second Life Release Candidate"
*** Unclean shutdown. ***
./secondlife: line 95: arch: command not found

Any ideas?

Thanks

---

### Post by Jabb3r on 2007-12-04
This is driving me mental. I've managed to iron out all the creases of me system except this one. I have tried everythin. I've never managed to run the SL slient once. Errors for precompiled or scons if I try and compile it myself. THis is the second system I've tried now and still not 1 successful attempt.

I've managed to get it to throw up a diff error now...

./secondlife
bin/do-not-directly-run-secondlife-bin: error while loading shared libraries: libELFIO.so: cannot open shared object file: No such file or directory
*** Unclean shutdown. ***


I've compiled a libELFIO.a and renamed it and put it around the system in places I thought it would want it /usr/lib etc but to no avail. Same error all the while I just don't know where it's looking.

I have not a clue how anyone can say "oh it should take 2 mins to get up and running" cause I just don't see how when we have pretty much same OS and I've installed all the things I've read about trying on me travels.

7.10 Gutsy Gibbon 64bit

Someone must know something?

---

### Post by MathaiosB on 2008-11-17
I know this is replying to an old message, but I am getting the same two errors on my system as this person and cannot find any fix for it. I've tried downloading the 1.21.5, the 1.21.6, and the 1.19.0.5 viewers and even used the cool viewer updates to the 1.19.0.5 client version. Always the same error, which tells me it's something wrong within Ubuntu, and not in the client. From what I can tell by looking through the shell script it's seg faulting at the line that's supposed to start sl, and then giving the "arch" not found when it gets down a few more lines.

This is on a 64 bit version of the 8.04 or 8.10 release of Ubuntu. I'm sure this has to be something simple, but I don't know what I'm missing here.

Oddly enough, when I ran Ubuntu 8.04 in VmWare under Windows Vista 64, I downloaded the linux client viewer and it ran without any hitches.

---

