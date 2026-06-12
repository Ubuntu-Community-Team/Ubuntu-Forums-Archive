---
title: "Remove Evolution Entirely!"
date: 2007-02-27
forum: Desktop Environments
---

### Post by Nanovox on 2007-02-27
Hey all, I have to admit I'm only 3-months into using Ubuntu.  I've recently wiped my server which previously had Fedora Core 1 and 2 on it for a few years.  After finding how unstable FC6 was, I decided to try Ubuntu.  While I'm not impressed with the package selection, I generally like it.

The first thing I did after installing this thing was to uninstall Evolution.  I absolute hate bloated programs like that.  Apparently, Evolution is like the Office of linux.  You can never quite get rid of it.  I figured an 'apt-get remove evolution' would be enough to get rid of all its data.  I was wrong.

First, in gconf-editor, Evolution entries sit quitely in the apps/ section.  How do I trash these?

Secondly, in the gnome-session-properties, under 'Startup Programs', '/usr/lib/evolution/2.8/evolution-alarm-notify' remains even though the /usr/lib/evolution folder doesn't even exist anymore.  Talk about a nice security hole.  And I can't seem to remove it because removing it is disabled.  So how do I delete this?

Are there spots that others have seen evolution's guts laying around?

---

### Post by aidanr on 2007-02-27
i think removing /etc/xdg/autostart/evolution-alarm-notify.desktop will solve problem 2, but the first one i'd also like to find an answer to, there are several programs that leave stuff behind in gconf (banshee, compiz, celestia, kiba dock etc) that i can't find a way to remove :-k

---

### Post by Quillz on 2007-02-27
Did you try running ```
sudo apt-get remove --purge evolution
``` and then running ```
apt-get autoremove
``` after that? The first option will remove a program and all of its preferences, and the second option removes all dependencies that relied on said program but serve no other purpose on your system.

---

### Post by Nanovox on 2007-02-27
I had run 'apt-get remove evolution', and that got rid of all dependencies.  I did not use the --purge option, and that does not seem to do anything after the fact.

Part of the problem I think is that gnome-panel depends on a few of the evolution libraries like the calendar and data server libraries.

---

### Post by Nanovox on 2007-02-27
> **aidanr said:**
> i think removing /etc/xdg/autostart/evolution-alarm-notify.desktop will solve problem 2, but the first one i'd also like to find an answer to, there are several programs that leave stuff behind in gconf (banshee, compiz, celestia, kiba dock etc) that i can't find a way to remove :-k

Thanks, aidanr.  Removing that file allowed me to remove the startup program from the list.

---

