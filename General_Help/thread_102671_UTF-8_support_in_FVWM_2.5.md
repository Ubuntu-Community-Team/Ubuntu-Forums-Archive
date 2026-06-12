---
title: "UTF-8 support in FVWM 2.5"
date: 2005-12-12
forum: General Help
---

### Post by michux on 2005-12-12
Hello. I just installed FVWM from official Ubuntu repositories (apt-get install fvwm). I have a problem with UTF-8 support in window titles and menus.

Screenshot here: [http://jakilinux.org/tmp/fvwm-crystal-no-utf8.png](http://jakilinux.org/tmp/fvwm-crystal-no-utf8.png)

I'm using the fvwm-crystal theme. But the problem doesn't seem to be crystal-related.

Any hints will do. I hope I just don't need to recompile fvwm with UTF-8 support, but it should be compiled in the official packages, shouldn't it?

---

### Post by michux on 2005-12-12
I just read some tips for Debian and FVWM:
[http://melkor.dnp.fmph.uniba.sk/~garabik/debian-utf8/HOWTO/howto.html](http://melkor.dnp.fmph.uniba.sk/~garabik/debian-utf8/HOWTO/howto.html)

It tells to change a line in 
 /usr/X11R6/lib/X11/locale/en_US.UTF-8/XLC_LOCALE file.
But I don't have the folder for my locale (pl_PL.UTF-8) there. Neither does it exist in /usr/share/X11/locale/

Is it normal? Maybe the thing is of no importance at all. The bug mentioned existed in 2003.

---

### Post by topyli on 2007-01-06
From the [polishlinux.org FVWM-Crystal page]("http://polishlinux.org/apps/fvwm-crystal-speed-and-transparency/"):

> If you use UTF-8 encoding in your system (and this is the default in some distros like Ubuntu or Fedora Core), you will need to manually edit a few configuration files so that the Unicode-specific letters show up as they should. Everywhere you encounter a line like that: ```
Font "xft:Tahoma:pixelsize=13"
```, you should change it to something like ```
Font "xft:Tahoma:encoding=iso10646-1:pixelsize=13"
``` and save the file.In practice, I've only had to edit window decoration config files so far.
There's also a [patch]("http://polishlinux.org/apps/fvwm-crystal-and-utf-8/") which fixes UTF-8 for FVWM-Crystal but I haven't tried it.

All in all, I'm [very happy]("http://img407.imageshack.us/my.php?image=screenshot200701070026km0.png") with my FVWM/GNOME setup.

---

### Post by michux on 2007-01-06
> **topyli said:**
> From the [polishlinux.org FVWM-Crystal page]("http://polishlinux.org/apps/fvwm-crystal-speed-and-transparency/"):

In practice, I've only had to edit window decoration config files so far.
There's also a [patch]("http://polishlinux.org/apps/fvwm-crystal-and-utf-8/") which fixes UTF-8 for FVWM-Crystal but I haven't tried it.

All in all, I'm [very happy]("http://img407.imageshack.us/my.php?image=screenshot200701070026km0.png") with my FVWM/GNOME setup.

That's actually the patch I wrote as a workaround.
Anyway thanks for mentioning :)

---

