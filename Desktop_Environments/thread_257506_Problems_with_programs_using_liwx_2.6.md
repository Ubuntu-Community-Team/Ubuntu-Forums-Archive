---
title: "Problems with programs using liwx* 2.6"
date: 2006-09-14
forum: Desktop Environments
---

### Post by KalasMannen on 2006-09-14
I recently noticed that i was unable to start my VLC mediaplayer. I get a segmentationfault whent trying to start it, now i've noticed that that wasn't the only program that refused to start.

I also have Xchm, wich also segfaults suddenly when i try to start it. I tried to figure out what was wrong, and i think that the only thing these programs has in common is that they depend on libwxgtk2.6-0. This makes sense, since i think that that particular package was updated last time i ran the updater. 

Now, how do i get this lib working again? I've already tried reinstalling, completely remove and install again, but always the same result. Also, this seems to be a issue that only occours on my particular machine, since i have other computers running Ubuntu that have the same versions of the packages installed and runs fine with VLC and Xchm.

Anyone that has any ideas?

---

### Post by lamego on 2006-09-14
Are you sure you didn't got the update from some unoffical repository you may have on your list ?
I don't remember seeing any libwxgtk2.6-0 upgrade on my system.

---

### Post by KalasMannen on 2006-09-14
Well, im almost certain. The only unofficial repos that i have are Videolans Nightlies, and the repository for Xgl and compiz ubuntupackages.

This is really annoying, since i know that these two programs worked perfectly before, and then suddenly one day they just refuse to start! ](*,)

---

### Post by lamego on 2006-09-14
Just if you want to check the package version:

> lamego@lamego-desktop:~/_software$ dpkg -l libwxgtk2.6-0
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  libwxgtk2.6-0  2.6.1.2ubuntu2 wxWidgets Cross-platform C++ GUI toolkit (GT


---

### Post by KalasMannen on 2006-09-14
Hmm, that is an exakt match of the version i have, so it's not related to a broken package, but rather something local on my machine.. :(

---

