---
title: "lxsession-edit changes don't stick"
date: 2012-03-07
forum: Desktop Environments
---

### Post by spadewarrior on 2012-03-07
Hi all,

I'm having difficulty getting the right applications to run when I log-in to LXDE. 

I'm trying to make Network Manager load by default, but the changes to the tick-boxes I make in lxsession-edit aren't reflected when I select 'OK' and re-open it, nor when I log-out and in again. Running it with the 'sudo' prefix doesn't help

Here's the output, should it be illuminating (it isn't to me):
[PHP]
$ lxsession-edit 

(lxsession-edit:2239): Gtk-WARNING **: Unable to locate theme engine in module_path: "ubuntulooks",
** (lxsession-edit:2239): DEBUG: src:/etc/xdg/autostart/nm-applet.desktop, save to: /home/thingy/.config/autostart/nm-applet.desktop
[/PHP]

---

### Post by spadewarrior on 2012-03-08
Bump...?

---

### Post by Rodney9 on 2012-03-08
[http://goo.gl/BiSx8](http://goo.gl/BiSx8)


For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by spadewarrior on 2012-03-10
Ah cheers, you rule.

---

