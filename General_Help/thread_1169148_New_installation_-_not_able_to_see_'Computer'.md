---
title: "New installation - not able to see 'Computer'"
date: 2009-05-24
forum: General Help
---

### Post by joshjosh on 2009-05-24
Hi,

I am new on this OS, but wanna give it a try and learn new things...got some issues...please I need your assistance...

I just load ubuntu from scratch, 9.04. and chose manual partition...hehe just to learn with my errors! (I am newbie and dont bother me to re-install if neede but to learn in the process!)

Here is my configuration as far I was reading on the web:

Partitions:

1. type: primary, location: beginning, use as: ext2 fs, mount point: /
2. logical, beginning, ext2 fs, /usr
3. logical beginning, swap, ---.
(swap size is 2x of my RAM)

Now, I got into OS after installation finished but when clicking on Places >> computer, the mouse icon starts loading but nothing happens...

I also tried to click on: Places >> home and nothing happens either!

what could be wrong?? any suggestions...thanks!

---

### Post by CatKiller on 2009-05-25
Do you get any informative error messages if you run **nautilus** from a Terminal?

---

### Post by joshjosh on 2009-05-25
No messages at all, only it doesnt load the computer browser...

I tried **nautilus** command and got same results.

But got it resolve!

I did reinstall again but this time I added a partition for /var, /boot and /temp and after loading up the OS again, all was working as desired.

Now, **nautilus** command works as a sharm!

Thanks anyways, but does anyone know what cause my issue? are those directories so important? what I notice is that this time it took longer to finish the installation...could be that?

---

