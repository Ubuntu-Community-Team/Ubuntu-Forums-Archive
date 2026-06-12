---
title: "Problem reaching Grub"
date: 2012-01-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by alexander- on 2012-01-06
Hi Everyone,

Been working on a problem for a while but i've ran out of ideas on how to fix it. Hoping someone here can help me.
Let me start with saying that im pretty new to Ubuntu.

Problem started with an error message approximately 10 secs after startup of the server (Dell PE SC 440).
"kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"

Unless im totally wrong here, i need to change kernel-order or kernel-version (or something like that) in Grub.
But the problem is, and i guess this has turned into the main-problem, that i cannot reach/see Grub at startup.
I've been booting the server with a live-cd, and changed in /boot/grub/menu.lst . I put the timer on 8 and made it so grub shouldnt be hidden. However, i still cannot see it.
Tried to press Esc from startup, but it still wont appear. Just the same error message after a while.

So, i tried to reinstall it using this guide (got encrypted LVM drives): [http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/](http://stephentanner.com/index.php/2011/05/restoring-grub-for-an-encrypted-lvm/)

But still same problem after a reboot.

Any ideas on what i possibly could do wrong would be appreciated!

---

