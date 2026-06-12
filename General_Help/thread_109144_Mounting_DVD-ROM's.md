---
title: "Mounting DVD-ROM's"
date: 2005-12-27
forum: General Help
---

### Post by uab999 on 2005-12-27
I recently installed Ubuntu 5.10.  When I first placed a DVD into my drives, the drives were showing up.  However, something happened and now the drives d not show up at all.  I was able to mount them manually in the terminal, but when I restart the drives no longer show up anymore.  How can I get the drives to mount during boot?

---

### Post by sciurus on 2005-12-27
Is gnome-volume-manager running?

---

### Post by uab999 on 2005-12-27
yes it is running

---

### Post by stuporglue on 2005-12-28
After inserting the DVD, does the drive at least spin up? What is the output of dmesg after the drive is done spinning up? 

Open a terminal and type: "dmesg"  
If the last ~10 lines look relavant, paste them here.

---

### Post by stevea1210 on 2005-12-30
Do you have your system up to date?  This sounds like an issue that was fixed with an upodate to pmount.

---

