---
title: "Completely lost...."
date: 2005-12-28
forum: Desktop Environments
---

### Post by DarkDancer on 2005-12-28
Hi!

I have a NetGear wg311v3 wireless card and a nice fresh install of Unbutu. I know I need ndiswrapper-util, and I think I have it (I downloaded ndiswrapper-utils_1.1-4_i386.deb). I went to the wiki and read what it said there and that all went way over my head, what do I do?

---

### Post by anil_robo on 2005-12-28
Once you have downloaded a .deb file, you can open a terminal, browse to the directory where you have downloaded it using the cd command, and then when you reach the directory containing the .deb file, simply type this:
```
sudo dpkg -i name-of-deb-file.deb
```
This will install the deb package.

---

### Post by DarkDancer on 2005-12-28
Ok, tried that, and failed. I think it is because Ubuntu is loaded on hda3, and ndiswrapper is on hda 5, and I don't know how to get to hda5. I tried cd /hda5, but it errored on me.

---

### Post by DarkDancer on 2005-12-28
Ok, I see I'm in the wrong place, where is the absolute beginner area?

Ok, never mind found it, moving over there, sorry for the intrusion.... ;)

---

