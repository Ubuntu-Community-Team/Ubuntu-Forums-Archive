---
title: "GTK not themed after downgrade from gnome3 ppa to unity"
date: 2011-05-03
forum: Desktop Environments
---

### Post by arcterex on 2011-05-03
So here's what I did:
[LIST]
[*] upgrade to 11.04
[*] decided I didn't like unity, wanted to try gnome3
[*] installed from the gnome3-team/gnome3 ppa
[*] it didn't work (only a blue screen on login)
[*] fought with it a bunch, did some install and removing to try to get things working
[*] downgraded via the ppa-purge command documented elsewhere
[*] copied my /usr/share/xsessions/* files from another computer to allow me to login
[*] made sure I was up to date with all the normal ubuntu packages
[/LIST]

After a bunch of fighting I'm able to log in and everything seems to be working except that all my GTK apps (ie: nautilus) don't seem to get the controls themed.  Changing the theme in the appearance applet just doesn't have an effect on the controls or icons.  The window titles get themed, but not the rest of it.

Any thoughts?  Another (possibly) related thing is that I had to re-install gnome-session and a couple of other packages (comparing my system to a VM that has 11.04 installed cleanly).

What controls gtk themeing?
What packages or config might I be missing?

TIA all.

---

