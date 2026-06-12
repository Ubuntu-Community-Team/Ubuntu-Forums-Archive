---
title: "Lucid Lynx - E17 distro?"
date: 2010-06-16
forum: Desktop Environments
---

### Post by danbuter on 2010-06-16
It seems the majority of Enlightenment distros are based on Debian, and way out of date. Is there one that is based on LL, or Sid?

If not, is there a way I can build my own from the minimilist CD?
Thanks!

---

### Post by wojox on 2010-06-17
Sure I've done it from a minimal install.

When your done installing reboot and run:

```
sudo apt-get update; sudo apt-get install e17
```

You'll have to reboot and startx or install a login manager like SLiM

---

### Post by danbuter on 2010-06-18
I know I'd need more than just e17. I don't know what the "List" of programs is that I'd need to get a functional OS, though.

---

### Post by earthpigg on 2010-06-18
> **danbuter said:**
> I know I'd need more than just e17. I don't know what the "List" of programs is that I'd need to get a functional OS, though.

apt-get install firefox synaptic empathy (or pidgin) gdebi remastersys jockey-gtk wicd (or network-manager) gdm (or slim) ubiquity-frontend-gtk (ubuntu's graphical installer)

---

### Post by beastrace91 on 2011-04-08
Minimal Ubuntu Install+E17+Preconfigured to be fantastic = Bodhi Linux - [http://bodhilinux.com/](http://bodhilinux.com/)

[img]http://bodhilinux.com/images/frontsplash/bodhi2.png[/img]

~Jeff Hoogland

---

