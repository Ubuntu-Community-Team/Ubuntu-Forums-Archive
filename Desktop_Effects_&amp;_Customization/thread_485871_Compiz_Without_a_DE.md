---
title: "Compiz Without a DE"
date: 2007-06-27
forum: Desktop Effects &amp; Customization
---

### Post by redline6561 on 2007-06-27
Out of curiosity does anyone know whether it's possible to run compiz without a desktop environment such as Gnome, KDE, or XFCE? How much trouble would it be to do this and what supplemental applications might be required i.e. pypanel, $menuapp, etc?

---

### Post by smartboyathome on 2007-06-27
This would be like trying to use FVWM as a desktop enviroment. Take a look at FVWM-Crystal (*the* FVWM destop enviroment), it took a lot of work just to get it that far. That is about how much work you would need to get Compiz to run as a desktop enviroment.

---

### Post by jordanmthomas on 2007-08-01
It wouldn't be too much trouble and I've done it before:
[http://wiki.archlinux.org/index.php/Beryl#No_Desktop.2C_Beryl_as_window_manager_only](http://wiki.archlinux.org/index.php/Beryl#No_Desktop.2C_Beryl_as_window_manager_only)
(for beryl, but it works with compiz too...just substitute relevant names as neccessary)

I would suggest running pypanel or dmenu as well or set up xbindkeys and run it so you can launch programs.  (compiz is pretty useless without windows to manage, right?)

Of course, you can add any supplemental apps you want, so that's a matter of opinion.  This link is for if you don't use gdm (like myself), but it should be pretty straightforward to set this up with gdm (just find out how those .desktops are laid out and make a script as described as in my link.)

---

