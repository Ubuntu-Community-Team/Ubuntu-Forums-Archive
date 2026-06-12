---
title: "how do I uninstall Eternal Lands"
date: 2009-04-13
forum: Gaming &amp; Leisure
---

### Post by Jatchie on 2009-04-13
Hello.
I am new to Ubuntu 8.10 64. I am wondering how do I uninstall Eternal Lands please.

---

### Post by TheBuzzSaw on 2009-04-13
Unless you installed it using some special installer, you should be able to just delete the folder you extracted it to.

---

### Post by Jatchie on 2009-04-13
I installed it using script in Terminal.

---

### Post by miegiel on 2009-04-13
Take a look at the script (in  a text editor). If it doesn't make sens to you maybe it will to someone else when you post it here.

---

### Post by Jatchie on 2009-04-14
I think I got it.

I opened terminal cd/usr/games
sudo rm enternallands.
I just hope that removes all of it. Thank You all for the help :p

---

### Post by pjbroad on 2011-04-29
If you installed the packages via the install script, then to un-install use:
sudo apt-get remove eternallands

---

