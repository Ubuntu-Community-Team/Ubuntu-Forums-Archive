---
title: "Help! KDE screwed up my install!"
date: 2010-01-11
forum: Desktop Environments
---

### Post by linuxnerd1 on 2010-01-11
Ok, I installed the kde-desktop package on Ubuntu 9.10. And I loved it :D.

I shut down my PC, then when I got back home and I booted up Ubuntu, went to the bathroom and saw a distorted what looked like an error messagage :(.It had a triangle with an ! in it. I had to shut it down. Now I am in Windows.

Is there any way to fix this without a reinstall or even worse, a reformat?

---

### Post by MooPi on 2010-01-11
You'll need to be more specific for us to help you. What did the message say ? What did you do prior to shutting down last ? Any detail would help ?

---

### Post by nerdy_kid on 2010-01-11
> **MooPi said:**
> You'll need to be more specific for us to help you. What did the message say ? What did you do prior to shutting down last ? Any detail would help ?

he said it was distorted.....




sounds like a kdm issue:
start ubuntu, and when it looks like its done loading, press <ctrl><alt><F1>.  This will bring you to a terminal.
login, then do
```

sudo dpkg-reconfigure gdm

```
and select gdm as the primary display manager.
then do
```

sudo reboot

```
that will hopefully get you to a login screen at least.

---

