---
title: "Getting Le Conjugueur to run (an update)"
date: 2015-08-03
forum: Desktop Environments
---

### Post by Tom_ZeCat on 2015-08-03
This is an update to this previous thread: 
[http://ubuntuforums.org/showthread.php?t=2205780&p=12930375#post12930375]("http://ubuntuforums.org/showthread.php?t=2205780&p=12930375#post12930375")

Quick recap: Le Conjugueur, a French verb conjugating program, is abandonware last developed for Ubuntu 8.04.  Previously, I had problems getting it to run in Kubuntu 13.04 because it was missing a 32-bit dependency no longer provided in *buntu/64.  The previous solution was to add this by doing this in the terminal: 

```
sudo apt-get install libgtk2.0-0:i386
```

This worked in Kubuntu 13.04/64 through 14.10, but, turns out it's not enough for Kubuntu 15.04 (and probably other *buntus).  To get it to work in 15.04, I had to do the command I just listed, plus the following one: 

```
sudo apt-get install lib32stdc++6 lib32z1 lib32z1-dev
```

I'm posting this for the benefit of others who may be googling a solution.  I'm delighted to have LC running again.  I'm disappointed it's no longer developed for Linux, but at least I don't have to stop using this version.

Edit: I should include the error message I got so that it's easier for people to find this via a search.  When I first installed Le Conjugueur via its Debian package, it would not run.  When I tried running it in the terminal, I got this message: 

> leconjugueur: error while loading shared libraries: libstdc++.so.6: cannot open shared object file: No such file or directory

The second set of code that I posted fixed that.

---

### Post by Vladlenin5000 on 2015-08-04
Many similar tools aren't around anymore either.
Reason: All those resources are in the web so why have a dedicated app?

---

