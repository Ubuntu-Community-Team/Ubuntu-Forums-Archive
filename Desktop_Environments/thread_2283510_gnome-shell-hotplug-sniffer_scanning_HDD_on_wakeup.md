---
title: "gnome-shell-hotplug-sniffer scanning HDD on wakeup"
date: 2015-06-22
forum: Desktop Environments
---

### Post by Oracle_The_Blind on 2015-06-22
Hi,

I have two drives in my computer: A main SSD and a large, infrequently used HDD which is usually in standby (spun down).
When I leave my computer, I press a shortcut key to turn off my monitors which executues:
gnome-screensaver-command -a

When I come back and press any key to turn the monitors back on, the magnetic drives spins up! This is the problem.

Digging in by running fatrace, I see that when the computer comes out of screensaver, gnome-shell-hotplug-sniffer accesses basically every directory on the HDD. I assume this is what is causing it to spin up.
If I delete the gnome-shell-hotplug-sniffer executable the drive does not spin up. (win!). However, this seems like quite a rude thing for me to do...

Questions:
What is gnome-shell-hotplug-sniffer? I can't find any docs on it.
Why is it scanning my HDD when the computer comes out of screensaver? It seems to scan a few other system directories, but not much of the SSD.
How can I stop it doing this?

Thanks!
James

Additional info:
Ubuntu Gnome 14.04
Gnome version 3.12 from the GNOME3 Staging repo

---

