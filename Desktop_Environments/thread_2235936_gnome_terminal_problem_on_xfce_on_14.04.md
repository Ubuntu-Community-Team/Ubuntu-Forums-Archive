---
title: "gnome terminal problem on xfce on 14.04"
date: 2014-07-23
forum: Desktop Environments
---

### Post by kmand on 2014-07-23
I'm running standard ubuntu 14.04 desktop. This is an older machine with older Nvidia graphics and limited Nvidia memory. While I like Unity, Compiz uses up too much of the Nvidia memory which I need when I run a multimedia program.

So I added an xfce session with "apt-get install xfce4". Now I can choose either Unity or Xfce at login depending on my need. However, the default terminal when I click on the terminal icon,  comes up as the gnome-terminal and shows a blank black background.

I can use an xterm but do prefer the gnome-terminal. If I invoke gnome-terminal from the xterm command line, I get

GLib-GIO-CRITICAL **: g_settings_get: the format string may not contain '&' (key 'monospace-font-name' from schema 'org.gnome.desktop.interface'). This call will probably stop working with a future version of glib

and the same gnome-terminal with just black inside.

What am I missing. I'm not sure I added xfce correctly and probably there are other issues I'm not aware of.

---

### Post by ajgreeny on 2014-07-23
If you run xfce you will probably also have the xfce4 settings-manager available to you in which you can use the Preferred Applications.  I think that should make xfce4-terminal the default when running an xfce session.  You might also like to change the other default applications in the same way.

---

### Post by Bucky Ball on 2014-07-23
You installed xfce4 fine. I prefer lxterminal, which works great with xfce4. xfce4-terminal does exist, but not sure if it's default. It is not installed in my xfce4 install. I have xterm as the default by the looks.

---

