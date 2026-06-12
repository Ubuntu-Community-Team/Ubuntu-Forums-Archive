---
title: "gnome-session-save does not exist on my system (11.10)"
date: 2012-01-18
forum: Desktop Environments
---

### Post by DavidBiesack on 2012-01-18
gnome-session-save does not exist on my system (11.10) and

[INDENT][FONT="Courier New"]sudo apt-get install gnome-session-save[/FONT]
[/INDENT]
does not work, either.

What command does the logout option under my name in the gnome-panel applet use? Can I change it?

For example, I run vmware and when I log out, I want to run a vmware-suspend script I have which sends a HUP to the vmware player and waits for it to close before exiting; this helps prevent corrupting the player.

---

### Post by oldos2er on 2012-01-18
Post moved to its own thread.

---

### Post by Krytarik on 2012-01-18
Since Oneiric 11.10, it's "gnome-session-quit", part of the package "gnome-session-bin" (same as was "gnome-session-save" previously), installed by default, obviously:

[http://manpages.ubuntu.com/manpages/oneiric/en/man1/gnome-session-quit.1.html](http://manpages.ubuntu.com/manpages/oneiric/en/man1/gnome-session-quit.1.html)

Regards.

---

