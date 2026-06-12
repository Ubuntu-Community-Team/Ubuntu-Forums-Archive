---
title: "MAME roms that worked in Windows don't  in Ubuntu"
date: 2007-05-07
forum: Gaming &amp; Leisure
---

### Post by bokorpop on 2007-05-07
I am a big MAMer, and recently switched to Ubuntu. While many games do work, most fighting games(including the street fighter series) do not seem to work in MAME. I get an error message about missing ROM files, when the same set of ROM files worked perfectly fine in Windows XP. I also get an "LIRC disabled" message as well.

What is LIRC, and why don't fighting games work with MAME in ubuntu? Can any fellow MAMers out there attest that they do work and tell me how to make it happen?

---

### Post by gaspar on 2007-05-07
What mame are you using? I'm using sdlmame and wah!cade front-end, and after some problems, it's running ok...

---

### Post by retrorob on 2007-05-07
I have built a couple of MAME arcade machines and have had this problem from time to time:

Check the files inside the zips to see if the roms are named Exactly as they are in the errors. Capitalization Matters!

Also note that the ROM requirements change from version to version of mame -- make sure you are using ROMS that match your version.

---

### Post by DoktorSeven on 2007-05-08
In kxmame: Go to the rom in the list, right click, properties.  Hit Audit beside Rom Check to see if the ROM is good according to the version of xmame installed.

---

