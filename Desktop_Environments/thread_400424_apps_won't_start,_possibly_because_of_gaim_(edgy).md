---
title: "apps won't start, possibly because of gaim (edgy)"
date: 2007-04-03
forum: Desktop Environments
---

### Post by tengil on 2007-04-03
Hi,

Trying to get edgy up for gf but are having some problems.

After a while after logging in (in gnome) many applications won't start. Terminal, gedit, open office, gaim, etc, won't start. The wheel spins for a while then nothing. After restarting gdm all is fine (until it breaks again).

It looks like this is happening after gaim has been used.

There is nothing in the syslog.

Grateful for any help.
Thanks.

---

### Post by CrazyGenie on 2007-04-05
Logout of your Gnome desktop, go to a shell and move all your .gnome* and .gconf* files to a temporary location (or tar them up). Then come to GDM Login screen, select the session as "Default system session" and language as "System default" from GDM Login screen options. Then, login and check. This might, work in case there is some conflict in your .gconf and .gnome configurations. Remember that you will get a Gnome desktop with default settings!!

Example;
tar -zcvf gnome-config.tar.gz .gnome* .gconf*
rm -r .gnome* .gconf*
exit

---

### Post by tengil on 2007-04-05
Thanks for the suggestion.

Unfortunately it didn't help. It looked promising for a while but when gaim had been running for an hour or two, after I quit it, the problems came back. Can't start the apps. Also, the system update icon (the orange one) in the tray also disappeared along with the gaim icon when I quit gaim. This does not affect all apps. Gimp for example has no problems starting, but terminal, gedit, open office and others won't come up.

---

