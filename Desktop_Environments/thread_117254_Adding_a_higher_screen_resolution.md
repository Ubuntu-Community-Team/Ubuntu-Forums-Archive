---
title: "Adding a higher screen resolution"
date: 2006-01-14
forum: Desktop Environments
---

### Post by Noelinho on 2006-01-14
Hi all,

I've just invested in a new monitor which goes up to 1280 x 1024 screen resolution. My previous monitor only did up to 1024 x 768, and so I disabled all other screen resolutions. How do I now add 1280 x 768 so I can use this resolution on my new monitor?

---

### Post by dcstar on 2006-01-14
[QUOTE=Noelinho]Hi all,

I've just invested in a new monitor which goes up to 1280 x 1024 screen resolution. My previous monitor only did up to 1024 x 768, and so I disabled all other screen resolutions. How do I now add 1280 x 768 so I can use this resolution on my new monitor?[/QUOTE]
Either directly edit your xorg.conf file, or:

sudo dpkg-reconfigure xserver-xorg

to let Ubuntu redetect what the monitor can now do.

---

### Post by oakz on 2006-01-14
sudo dpkg-reconfigure xserver-xorg

---

