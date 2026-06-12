---
title: "Mate Killed my 12.04"
date: 2013-11-06
forum: Desktop Environments
---

### Post by amhainen on 2013-11-06
I'm running Ubuntu 12.04. I had XFCE, LXDE, Cinnamon, and Unity (or Gnome?) Fallback installed since 12.04 came out (in the case of Cinnamon, whenever it was readily available). Everything ran fine and then I wanted to try Mate. Bad idea! When I installed Mate, my audio broke, my display is all messed up. If you look at the print screen I took, windows aren't clearing from the desktop and a lot of the opacity items (particular on the menu bar in Unity) go to white instead of opaque.

I tried changing my grub config to nomodeset per [this forum]("http://ubuntuforums.org/showthread.php?t=1478319"). That made things revert to some low resolution like 800x600 or something.

Does anyone know how I could fix what I did? Perhaps a 'sudo apt-get purge mate' and then reinstall Ubuntu desktop?? Thanks for the help.

[IMG]http://i.imgur.com/WoyB5Hj.png[/IMG]

---

### Post by ag4032 on 2013-11-06
In case you added mate through ppa, there's a ppa-purge-tool:  [http://www.theorangenotebook.com/2012/01/ppa-purge-magic-undo-buttton.html](http://www.theorangenotebook.com/2012/01/ppa-purge-magic-undo-buttton.html) . I must add I haven't used it myself.

---

### Post by buzzingrobot on 2013-11-06
If you wanna try again, follow the directions at the MATE site: mate-desktop.org.  I've installed MATE on every Ubuntu release since 12.04 with no problems.

---

