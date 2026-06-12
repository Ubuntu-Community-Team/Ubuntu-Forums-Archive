---
title: "Set dpkg-reconfigure gdm non-interactively?"
date: 2013-05-16
forum: Desktop Environments
---

### Post by victorhooi on 2013-05-16
Hi,

I'm trying to use Salt to configure a Ubuntu Gnome desktop.

I've installed Gnome Shell and GDM.

Normally, I'd use "dpkg-reconfigure gdm" in order to set gdm as the startup display manager.

However, if I'm using Salt, I need to find a way to do this non-interactively.

Is there such a way?

Cheers,
Victor

---

### Post by dino99 on 2013-05-16
maybe something like :  salt '<target>' <function> [arguments]
[https://salt.readthedocs.org/en/v0.9.1/topics/tutorial.html](https://salt.readthedocs.org/en/v0.9.1/topics/tutorial.html)

---

