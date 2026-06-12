---
title: "Problems installing printer driver. csh required..."
date: 2009-06-02
forum: General Help
---

### Post by xutkm on 2009-06-02
Hi all,

I'm a Windows user who is fed up with expensive licences and want to try Linux for a change.
I have run into problems right away.
Printers!
I have found drivers for my Brother DCP-117C and I'm trying to follow the instructions on how to install them.
I have succeeded with the LPR-driver but the CUPS wrapper gives me a hard time...
This is what I do:
kim@kim-laptop:~$ sudo dpkg -i --force-all --force-architecture cupswrapperMFC210C-1.0.2-3.i386.deb

And this is the result...

 ****** ERROR: csh is required. ******

How do I install csh? I believed that C-shell was always installed?
Help a novice please!!!

/Kim

---

### Post by plucky on 2009-06-02
```
sudo apt-get install tcsh
``` will install csh.


This [thread](http://ubuntuforums.org/showthread.php?t=590793) might help.

Good Luck

---

### Post by xutkm on 2009-06-02
Thanks a lot!
That did the trick! :D

---

