---
title: "Font problem in Gnome Tweak in 11.10"
date: 2011-11-13
forum: Desktop Environments
---

### Post by malty on 2011-11-13
Using 11.10 recently upgraded from 11.04

Running Gnome shell 3.2, logged in as gnome classic.
After running successfully for some days with a number of fonts I settled on Ikarius ADF bold italic as the default, ran this for several days, no problems, Today I gksudo nautilus in terminal and get...

john@john-Dimension-5000:~$ gksudo nautilus
Fontconfig error: "/etc/fonts/conf.d/10-antialias.conf", line 1: not well-formed (invalid token)
Fontconfig error: "/etc/fonts/conf.d/10-hinting-slight.conf", line 1: not well-formed (invalid token)
john@john-Dimension-5000:~$"

Now I cannot access any file as root in  Nautilus and returning, via Tweak to the default font set, after trying many different combinations, the screen fonts are all poorly formed and broken. 

I can login to Synaptic and Software centre OK


In Tweak the following are in place...........

Desktop...file manager on, remainder 0ff.

Fonts..text scaling factor...off
default..Ubuntu Bold 13
document...Ubuntu Bold 14
monospace...ditto
window title...ditto
hinting...full
antialiasing...greyscale

Window theme...Zuiktwo Dark
Shell theme, (here's a horse of a different colour, Tweak refuses to see the extensions even though all installed via WebUPD8's how to.)
Menu's have icons
Buttons have icons
Cursor theme...redglass
Keybinding theme...default
Icon theme...Faience ocre
GTK+ theme...high contrast inverse

11.10 has the latest updates and apart from above, looks good.

Have Googled but no results, any help please??

---

