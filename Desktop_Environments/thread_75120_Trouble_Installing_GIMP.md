---
title: "Trouble Installing GIMP"
date: 2005-10-13
forum: Desktop Environments
---

### Post by xynamax on 2005-10-13
I'm having a problem installing GIMP.  I couldn't find a .deb binary anywhere *hint*hint* ;) .

 So This is really only my second try at compiling a program....Opera was my first and that worked pretty OK.

So In the GIMP directory I ran:  

$./configure

and then after a while it failed with this error

checking for GTK+ - version >= 2.4.4... no
*** Could not run GTK+ test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK+ is incorrectly installed.
configure: error: Test for GTK+ failed. See the file 'INSTALL' for help.

now I've checked in Synaptic and I have libgtk2.0 version 2.8.3 and all the dev files and a TON of other GTK libraries that are probably unrealated (but I installed em anyway just in case).  I've also tried marking all my GTK libraries for REINSTALL and it didn't help anything.

I can post the whole compiler dump from the shell and I have the config.log but it really doesn't make much sense to me.

Please Help me out.  Thank you in advance.

XynamaX

---

### Post by mcduck on 2005-10-13
I just have to ask why don't you just install it with synaptic? Or the nice 'Add Programs'-thing from Applications-menu?

---

### Post by KingBahamut on 2005-10-13
Xyna, Gimp is on the Repositories just install it using Add/Remove Programs or Synaptic.

---

### Post by dcarpenter on 2005-10-13
Gimp is part of the breezy default install isnt it?

---

### Post by xynamax on 2005-10-13
you mean install the GIMP directly through a little program in GNOME??

that sounds almost too easy :p I'll give that a shot, I had no clue you could do that.  I'm such a linux n00b 

Thanks folks.  

Hey one other question... I keep seeing that Breezy Badger is out, but I downloaded a liveCD and subsequently an install ISO like 2 days ago...do I have a beta or an unstable release or something?

---

### Post by KingBahamut on 2005-10-13
More than likely its the Release Candidate that you have. When you do a dist upgrade next, youll be at offical release.

---

### Post by dcarpenter on 2005-10-13
What you have will most likely update to the "stable" release through the auto-updater program.  No need to download and burn a new ISO.

---

### Post by xynamax on 2005-10-13
Thanks so much.  :cool:

---

