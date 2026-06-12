---
title: "file ownership issue with ioquake3"
date: 2007-05-13
forum: Gaming &amp; Leisure
---

### Post by psyopper on 2007-05-13
Hello all,

I installed IOQuake3 this evening. Specifically after downloading it I ran the installer with the following 

sudo sh path/to/ioquake.run

It installed just fine but couldn't (or rather, wouldn't) read the QIII cd during the install. So I had to manually move pak0.pk3 from the cd to /usr/local/games/ioquake3/baseq3. Of course it didn't work natively in Nautilus so I attempted (ahem...cough cough) to chmod the directory. I don't think I did any damage but I couldn't move the file unitl I finally go smart enough to gksudo nautilus and drag and drop the file myself.

Here's the rub. Now none of the "shorcuts" work and the only way I can start ioquake is with "sudo ioquake" in the shell.

How doI fix this so that I can launch ioquake properly?

Thanks!!!

---

### Post by DoktorSeven on 2007-05-14
Possibly pak0.pk3 is only readable by root since you copied it over as root?

Try **sudo chmod 755 /usr/local/games/ioquake3/baseq3/pak0.pk3** (or whatever the exact path is) from the terminal.

---

### Post by psyopper on 2007-05-14
Thanks!

It was the /usr/local/games direcotry that was restricted. That did the trick!

---

