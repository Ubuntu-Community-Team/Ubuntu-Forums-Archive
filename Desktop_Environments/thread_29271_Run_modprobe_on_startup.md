---
title: "Run modprobe on startup"
date: 2005-04-23
forum: Desktop Environments
---

### Post by BigCdaAnswer3 on 2005-04-23
Hey all,
I had a working version of warty before which i upgraded to a working version of hoary, but i decided to backup my stuff, and reinstall a fresh, official hoary. Anyway, I have a HP pavilion laptop, and in order to get my mouse working before, I just added a quick little hack to the /etc/init.d/gdm file to do:

modprobe -r psmouse;
modprobe psmouse;

This didn't work anymore when I installed hoary, but it worked once I typed it in the terminal, so I'm guessing modprobe needs to be run as root upon loading to do this...I am not really sure the best way to do this....any suggestions?

---

### Post by heimo on 2005-04-23
Is the removal (-r) neccessary for this to work?

You can put modules to /etc/modules and they'll be loaded at startup.

---

