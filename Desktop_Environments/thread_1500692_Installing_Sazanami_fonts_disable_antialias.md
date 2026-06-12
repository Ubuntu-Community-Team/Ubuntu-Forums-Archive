---
title: "Installing Sazanami fonts disable antialias"
date: 2010-06-03
forum: Desktop Environments
---

### Post by lambengolmor on 2010-06-03
Hi all. I have this weird issue:

-ubuntu installation (english)
-installed italian and japanese languages through the language support
-set up antialias
---> everything works
-installed sazanami fonts through software center
---> antialias messed up (even for default sans font)

I tried
```

sudo fc-cache -f -v
sudo mkfontscale
sudo mkfontdir
sudo fc-cache
sudo dpkg-reconfigure fontconfig
```
as suggetsted [here]("https://wiki.ubuntu.com/Fonts"), restarted apps, log out&in, but nothing worked.

Finally I decided to operate a synaptic complete removal of the sazanami fonts and the antialias came back.

Is it supposed to be that way and I'm just missing some piece of info or it's a bug somewhere? I tested both on 32 and 64 bits installations: does anyone else experienced this problem?

EDIT: I did some other experiments and discovered the problem is only on the sazanami gothic package

---

