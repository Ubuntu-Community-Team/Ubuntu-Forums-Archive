---
title: "flat vs. gradiant toolbars appearing in LO for 2 different Xfce machines"
date: 2014-05-16
forum: Desktop Environments
---

### Post by timeofday on 2014-05-16
I have LibreOffice 4.2.3.3 installed on two machines, both with Xfce (LO is installed identically on both).  Machine 1 has Xubuntu 14.04; maschine 2 has Linux Mint 13 Xfce (which is based on Ubuntu 12.04 LTS). However, the LO toolbars look quite different between the two (see attached PNG; machine 2 toolbar at top, machine 1 at bottom)..

Machine 2 has nice flat toolbars, while machine 1 has ugly (to me) gradient toolbars. I would like to change them to flat. I've googled to no avail, and also asked on the LibrOffice forums and got no reply -- which makes sense, as this is not a configuration option in LO.

Has anyone a clue about this?

[ATTACH=CONFIG]253213[/ATTACH]

---

### Post by Adam_GUI on 2014-05-16
It almost looks like you're using the Greybird theme on the top picture, and a Clearlooks theme for the bottom.

This isn't a LibreOffice setting, it's an xfce setting.  If you had a different libreoffice setting, your icons would be different.

LO will use the system theme in its menu bar.
Like so: 
[ATTACH=CONFIG]253215[/ATTACH]

It's possible that you've used the default themes for both machines and they be using different themes,
that you've changed a theme on one machine and forgotten about it,
or that you have the same theme with a different version to account for the difference in packaging between the two installs.

You can change your XFCE theme under Settings Manager > Appearance > Style.

You may have to restart LibreOffice to notice your theme change.

---

### Post by timeofday on 2014-05-16
Found the problem!  My Xubuntu didn't have the "libreoffice-gnome" package installed -- when I installed it, LibreOffice now has nice flat toolbars.  Thank you (your reply steered me in the right direction)

---

