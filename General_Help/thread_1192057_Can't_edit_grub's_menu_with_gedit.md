---
title: "Can't edit grub's menu with gedit"
date: 2009-06-19
forum: General Help
---

### Post by Shinka.S on 2009-06-19
With;

```
sudo gedit /boot/grub/menu.lst
```

i get;

```
(gedit:12839): Gtk-WARNING **: cannot open display
```

vi works with [COLOR=Blue]sudo vi /boot/grub/menu.lst[/COLOR] but I have no idea how to use vi (and to be honest I'm not really interested).

---

### Post by swerdna on 2009-06-19
gksudo gedit etc

maybe, maybe not, just a passing thought

---

### Post by jocko on 2009-06-19
> **Shinka.S said:**
> With;

```
sudo gedit /boot/grub/menu.lst
```i get;

```
(gedit:12839): Gtk-WARNING **: cannot open display
```vi works with [COLOR=Blue]sudo vi /boot/grub/menu.lst[/COLOR] but I have no idea how to use vi (and to be honest I'm not really interested).
That looks like you are trying to start gedit without gnome running, or at least like you are trying to start it from a virtual console? That will obviously never work (gedit is a gnome program, and will never run without x and gtk...).

If that's the case, you need to run vi or nano (which is much easier to understand than vi).

---

### Post by themusicalduck on 2009-06-19
Found a couple of threads on the same problem:

[http://ubuntuforums.org/archive/index.php/t-166863.html](http://ubuntuforums.org/archive/index.php/t-166863.html)

and

[http://www.linuxquestions.org/questions/slackware-14/gtk-warning-cannot-open-display-182090/](http://www.linuxquestions.org/questions/slackware-14/gtk-warning-cannot-open-display-182090/)

First one is more recent so might be more relevant.

---

### Post by Shinka.S on 2009-06-20
> **swerdna said:**
> gksudo gedit etc

maybe, maybe not, just a passing thought

I saw gksudo elsewhere but I get;

[COLOR=Blue]bash: gksudo: command not found[/COLOR]

> **jocko said:**
> If that's the case, you need to run vi or nano (which is much easier to understand than vi).

Great,[COLOR=Blue] sudo nano[/COLOR] worked fine. Thank you !

---

