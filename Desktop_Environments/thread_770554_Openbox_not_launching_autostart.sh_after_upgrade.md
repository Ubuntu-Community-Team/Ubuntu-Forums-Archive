---
title: "Openbox not launching autostart.sh after upgrade"
date: 2008-04-27
forum: Desktop Environments
---

### Post by xerxesdaphat on 2008-04-27
Hihi,

Upgraded to 8.04 -- very nice, Gnome looks spiffy. I'm normally an Openbox user (pure Openbox, not just openbox-gnome etc.) however, so I'm rather perturbed by this.

It's no longer launching my autostart file, which was working just fine before upgrading. I've checked that GDM has got openbox-session in the /usr/share/xsessions/openbox.desktop file, not just openbox; however it's still not running the file. All my other openbox settings are there, just not autostart. Weirdly enough, hitting Alt-F2 and running openbox-session again runs my autostart.sh this time and everything is back to normal.

Anybody know what's going on?

Thanks.

EDIT: Just did an experiment and it seems like GDM isn't launching openbox-session despite me telling it to (I checked by putting a touch /tmp/foo.txt at the beginning of /usr/bin/openbox-session). It's only launching openbox itself it would seem.

---

### Post by uzusan on 2008-04-28
I've been having this problem as well since i upgraded to hardy and i was following this thread to see if anyone solved it. However, i've managed to fix mine.

The problem is that the session is set to just run the openbox binary rather than openbox-session.

To fix it, log out and change the session to Openbox Session rather than just Openbox. (it also fixed a problem i was having with the gnome-settings-deamon not running and my icons in thunar being default).

---

