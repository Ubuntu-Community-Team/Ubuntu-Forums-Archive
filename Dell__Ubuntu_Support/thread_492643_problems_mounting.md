---
title: "problems mounting"
date: 2007-07-05
forum: Dell  Ubuntu Support
---

### Post by grandpa2390 on 2007-07-05
I have an inspiron 1150 with a gig of ram. I got ubuntu 6 and 7 and have tried them both but i keep getting error messages. one of the common errors is that it has trouble mounting and then it has logical block errors. someone help me please

---

### Post by grandpa2390 on 2007-07-05
the error message i am receiving is:

invalid compressed format (err=1)
kernel panic-not syncing: VFS: unable to mount root fs on unknown-block (1,0)

---

### Post by neptho on 2007-07-05
It sounds like your grub settings are wrong.  If you've (re)installed Ubuntu over itself, this can happen.  Try going into the Grub menu by pressing 'esc' and press 'e' on the 'kernel=' line.  Change root=UUID=wewieroweroweriew(whatever) to root=/dev/sdaX or root=/dev/hdaX, wherever your root partition is (May be numbers 1 to 4).  Then, press 'b' to boot.  When it boots, edit /boot/grub/menu.lst and make the changes as you did above for root=/dev/sdaX, run 'sudo /usr/sbin/update-grub', and you should be A-OK.

---

### Post by grandpa2390 on 2007-07-05
well i havent actually installed it. I get so far as it to start loading everything and it has logical blocks

---

