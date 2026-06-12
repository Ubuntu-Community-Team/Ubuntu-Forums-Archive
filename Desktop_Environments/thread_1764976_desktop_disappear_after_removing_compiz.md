---
title: "desktop disappear after removing compiz"
date: 2011-05-22
forum: Desktop Environments
---

### Post by yaacovk on 2011-05-22
Hi
Ubuntu 11.04.
i removed the Compiz from my computer after thinking by mistake
that i don't need it anymore.
after rebooting the computer, the desktop disappear.
i'd try to install it again but without solving the problem.
someone can help me?

thanks in advance.

Yaacov.

---

### Post by Copper Bezel on 2011-05-22
Which login session are you using? That is, in the session menu that appears under the login window after you select your name? Are you using the default or the Classic mode?

When you say that your desktop disappeared, do you mean the desktop wallpaper, the panels, or something else?

---

### Post by yaacovk on 2011-05-22
> **Copper Bezel said:**
> Which login session are you using? That is, in the session menu that appears under the login window after you select your name? Are you using the default or the Classic mode?

When you say that your desktop disappeared, do you mean the desktop wallpaper, the panels, or something else?

sorry you right.
the panel disappear.
i'm login with my default administrator user without login screen.
the panel appear directly after the computer power on.

---

### Post by mcduck on 2011-05-23
Unity is a Compiz plugin, and thus requires you to run Compiz as the window manager.

If you choose the "Classic Ubuntu (no effects)" as your session in the login screen you should get into the old Gnome2 interface, where you can reinstall Compiz. After that you can open a terminal and run "unity --reset" to mae sure all Compiz plugins required by Unity are enabled and have sane settings so you can swich back to the default Unity desktop session again.

---

### Post by yaacovk on 2011-05-23
Thanks, but i resolve the problem in another way.
i opened the terminal and command:
unity --replace

the Terminal say that there is no unity installed on the system
and he suggest me install it by command:

sudo apt-get install unity

after i install, the system rebuild the panel.
during the installation the unity, the Terminal show many errors.
but after rebooting the computer the panel return back.

by the way, how i know the unity work o.k?

Regards.
Yaacov.

---

