---
title: "Tomboy notes import"
date: 2011-01-07
forum: Desktop Environments
---

### Post by gechert on 2011-01-07
Due to a computer failure I have a clean installation (10.10 64 bit. Gnome, Tomboy  1.4).

I am trying to copy my tomboy notes from my old hard drive. After some difficulty I found the “old” tomboy notes on the old HD under /home/../.local/share/tomboy, & copied them as root to a flash drive, despite an error msg saying something like “could not maintain ownership”.  And I then copied them to the same directory in the new cptr but tomboy won't recognize them,I thought due to ownership issue, but looking @ files in terminal they seem to have the same ownership & permissions as the notes I create on the new computer. Any ideas ?

---

### Post by ajgreeny on 2011-01-07
Why did you copy them as root to the flash drive?  That should not have been needed; you should have done it as your user.

How exactly did you do the copy, and when you look in the new location at the files, are you (as username) still the owner, with read/write, but with group and root having "read only" permissions?

---

### Post by sharm on 2011-01-09
You can read about how to manipulate file permissions here: [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Also, if you quit Tomboy, and then launch it from the terminal with `tomboy --debug`, you should get detailed error information explaining why it's failing to load your notes.  I'd also double-check that they are in ~/.local/share/tomboy/*.note .

---

