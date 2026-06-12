---
title: "can't open graphical interface"
date: 2009-04-11
forum: General Help
---

### Post by matteo123 on 2009-04-11
Hello,
Thanks for those who replied my last post.
I can't still use the graphical interface, only the command option. 
Some suggested to type "satartx"; it went as far as to the loading page of gnome,but then after some text this is what I got:

errors from xkbcomp are not fatal to the x server
(EE) config/hal:couldn't initialise context: (null) ((null))
Waiting for x server to shut down


Can somebody help?

---

### Post by spiderbatdad on 2009-04-11
possibly reinstall gdm and ubuntu-desktop
```
sudo apt-get install --reinstall gdm ubuntu-desktop
```

---

### Post by Berserker v7 on 2009-04-11
> **spiderbatdad said:**
> possibly reinstall gdm and ubuntu-desktop
```
sudo apt-get install --reinstall gdm ubuntu-desktop
```

Try executing the command ```
sudo gdm
``` from your terminal.

If that does not work, try ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Execute the quoted code as the last choice, as i believe it would reset the whole system.

---

### Post by matteo123 on 2009-04-11
Thanks for the replay, but i can't still open.
```
sudo gdm
```

i got error 116

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

i got "BIGIN failed"

and finally
```
sudo apt-get install --reinstall gdm ubuntu-desktop
```

i got "Unable to fetch some archives, maybe run apt-get update or try with --fix.missing?"
which i tried both option and no success

---

