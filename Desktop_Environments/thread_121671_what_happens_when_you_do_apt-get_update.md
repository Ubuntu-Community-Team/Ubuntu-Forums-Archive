---
title: "what happens when you do apt-get update?"
date: 2006-01-25
forum: Desktop Environments
---

### Post by neoflight on 2006-01-25
what exactly happens when u do apt-get update? upgrade? dist-upgrade?
every time (once a day) i do it(update)...it brings some data from some source...

why is it that so? i am using breezy....if its a stable release and y would it bring some packages/files/data in bits/bytes/mbs this frequently? 

are they really 'updates' ?  i noticed that sometimes i get some lib files which were not already installed? then thats a new install right? not update?

when i chose to see individual files in synaptic while i do 'reload' i see 'hit' for some files or 'failed' for others...failed as in not required or just failed to get something?

plus...i observed that while doing apt-get update linux-kernal image 2.6.12-10-386 is brought in...this happend more than once in a week :confused:  i already have that brought in a while back and i use the same kernal which i am sure by looking at uname -r.

any clues?

thanks

---

### Post by aysiu on 2006-01-25
*apt-get update* updates your repositories list--what's available, what you have installed.

*apt-get upgrade* applies updates to the applications you have installed.

*apt-get dist-upgrade* applies updates to the applications you've installed *and* installs applications your distribution thinks you should have installed as part of the new version. It may also remove packages viewed as obsolete or conflicting.

---

### Post by syklitengutt on 2006-01-25
its the list of possible innstallations (progs etc) that you can install with apt-get.
You only have to use apt-get update if you are going to install something to get the list of available progs up to date....

---

### Post by jasay on 2006-01-25
[QUOTE=neoflight]what exactly happens when u do apt-get update? upgrade? dist-upgrade?
every time (once a day) i do it(update)...it brings some data from some source...[/QUOTE]I'm a little fuzzy on this, so don't take it as scripture, but from what I understand . . . Update downloads a list of available packages from each of the repos in your sources.list file.  Upgrade compares that list to the list of software you have installed and downloads/installs any package that can just replace the old version of said package.  Dist-upgrade does a similar thing but tries to upgrade everything, even if it requires new dependencies or deletes old ones that are no longer needed.  This is most useful for upgrading say from Breezy to Dapper as there are major dependency changes between distro versions.
[QUOTE=neoflight]why is it that so? i am using breezy....if its a stable release and y would it bring some packages/files/data in bits/bytes/mbs this frequently? [/QUOTE]Breezy is considered stable, but there are still security updates (eg. if a hole is found in firefox a patched version is made available).  Also, if you have backports or (an) unofficial repo(s) enabled you'll get some of the newer software upgraded from there.
[QUOTE=neoflight]plus...i observed that while doing apt-get update linux-kernal image 2.6.12-10-386 is brought in...this happend more than once in a week :confused:  i already have that brought in a while back and i use the same kernal which i am sure by looking at uname -r.
[/QUOTE] The version I have is actually 2.6.12-10.26.  I'd guess the first time I got 2.6.12-10 it was actually something more like 2.6.12-10.24.

As for the other stuff, I'm not entirely sure.

---

