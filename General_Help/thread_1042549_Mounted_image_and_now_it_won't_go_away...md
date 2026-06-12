---
title: "Mounted image and now it won't go away.."
date: 2009-01-17
forum: General Help
---

### Post by steve04 on 2009-01-17
***Solved***


I used Furius ISO mount to mount a NRG file (to view the contents of it).  Now it is stuck on my desktop.  If I select to open it I get the error "There is no application installed for this file type."  If I try to unmount it I get the error "umount: /home/steve/Kings_Quest_7_ISO_(KQ7)_nrg is not in the fstab (and you are not root)."  When I run a sudo unmount command in the terminal it doesn't work because the file name contains ( ).  I also tried opening a folder as root then unmounting this drive but it doesn't do anything (not even an error).  Also when I go to the actual /home/steve directory where it says the file is, nothing is there (even when displaying hidden files).  Any ideas?

---

### Post by x33a on 2009-01-18
do a system restart and see if it's still mounted.

---

### Post by steve04 on 2009-01-18
Ok got it away doing that.   I was under the impression that a Ctrl+alt+backspace was the same as doing a reboot but apparently it isn't.  Thanks.

---

### Post by taurus on 2009-01-18
Ctrl+alt+backspace only restarts the X server.  Reboot means shut down all the running processes first and then start the computer again.

---

