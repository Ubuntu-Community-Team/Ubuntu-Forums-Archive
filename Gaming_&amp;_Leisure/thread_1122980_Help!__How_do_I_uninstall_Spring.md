---
title: "Help!  How do I uninstall Spring?"
date: 2009-04-11
forum: Gaming &amp; Leisure
---

### Post by jdunn on 2009-04-11
Spring TA would be a great game if the Spring lobby and Spring downloader didn't suck so much.  After an entire afternoon, I was only able to play one game.  the Spring downloader is torrent-based and wouldn't download maps most of the time, even though the port on my firewall was open.  On the Spring chat server, the community isn't very friendly or helpful.  Connecting to game servers was also problematic.  To top it off, game directories and files are strewn all over my /home/<user> directory.  Too bad...I heard this was one of the greatest RTS games for linux.  What a joke.  Now, I'm having trouble getting it off my computer.

How do I uninstall this game?  Synaptic won't list the installed files, probably because there is no public key.  I do a search on the install files (based on my update history) but nothing shows up.  Am I going to have to uninstall each of the 16+ packages from the command-line?

:mad::mad::mad::mad::mad::mad::mad::mad:

---

### Post by bobmatino17 on 2009-04-11
sudo apt-get remove -p <package name>

---

### Post by jdunn on 2009-04-11
> **bobmatino17 said:**
> sudo apt-get remove -p <package name>

I guess that answers my question "Am I going to have to uninstall each of the 16+ packages from the command-line?"  :(

---

### Post by Vadi on 2009-04-11
Synaptic should list the packages, search for "spring" in the package name. It lists them here :/

---

### Post by jdunn on 2009-04-11
> **Vadi said:**
> Synaptic should list the packages, search for "spring" in the package name. It lists them here :/

Synaptic did NOT list the packages (except in the update history).  A search for "spring" did not locate spring, even though the 3rd party repository was enabled.  I noticed Synaptic was complaining that the repository had no public key...That's probably why.

Anyway, its no longer an issue for me because I spent several minutes at the CL, successfully purging spring and the other installed dependencies from my computer.

---

