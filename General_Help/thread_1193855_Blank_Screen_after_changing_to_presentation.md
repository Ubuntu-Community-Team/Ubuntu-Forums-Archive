---
title: "Blank Screen after changing to presentation"
date: 2009-06-22
forum: General Help
---

### Post by WhiskyChris on 2009-06-22
I'm using ubuntu 9.04 on a dell laptop with integrated intel graphics. It has been working fine for many months now.

Earlier today I tried to give a presentation on a projector plugged into my laptop, unfortunately when trying to display on the external screen I changed some settings in Appearance - Display and now my laptop screen is blank apart from a cursor. I gave the presentation using a different computer and now need to restore my display settings.

Restarting the computer boots up with normal progress display. I don't see the login dialogue however I can login if I type my username and password (at least after typing them I see hdd activity).

Can someone help me restore the previous settings using one of the alternative command-line consoles (ie Ctrl-Alt-F4). I'm fairly confident with the command line, I just don't know what needs changing where!

Thanks.

---

### Post by WhiskyChris on 2009-06-22
Nevermind: just figured it out.

My /etc/X11/xorg.conf had been changed so that the desktop was only displayed on the external screen. Luckily it had backed up the old xorg.conf file and so an easy switch sorted it out.

---

