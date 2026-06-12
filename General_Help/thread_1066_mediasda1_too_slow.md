---
title: "/media/sda1 too slow"
date: 2004-10-18
forum: General Help
---

### Post by Snoopy on 2004-10-18
Hi there,

This morning I connected my Creative Muvo 64MB mp3 player to one of my USB slots, and a /media/sda1 (usb-storage) window popped right off. "Goody!", I thought, "No configuration needed".

However, when I tried to copy some mp3s to it, it went really slow. It took about 11 minutes to copy a 15MB file, which normally doesn't take any longer than a second or 15.

The files were copied successfully and they played fine, but the slowness is kindof problematic. Anyone else have any problems with usb-storage (such as digital camera or usb sticks) being slow?

---

### Post by Robin Mehner on 2004-10-18
Hello,

i have a Iriver HDD Player which is connected via USB. I encoutered some problemes with rythmbox playing files and copying between pc and player. Even this slowness effect appeared.

A friend of mine suggested to make a symlink in my home directory to /media/sda1 and it worked fine, all problems are away. But, honestly, i have no clue why :)

```

cd
ln -s /media/sda1 player

```

After this you have to access the player via the link in your home dir.

Hope it will work for you,
- Robin

---

### Post by Snoopy on 2004-10-19
Thanks, but no luck. :(

---

