---
title: "Problem with various App"
date: 2008-12-08
forum: General Help
---

### Post by 10up on 2008-12-08
I'm incredibly new to Ubuntu and Linux/Unix based systems.  Recently installed Ubuntu 8.10 on an old computer.

For some reason whenever I try to start up various applications (Terminal, Add/Remove, System Monitor) an empty white box appears where the application would be opening and nothing else happens.

The same thing happens when I try to install anything new, such as AV Codecs, Adobe Flash, any updates.

I have noticed that if I have Terminal "open" (meaning the blank white box is on the desktop) and I restart, right before the console shuts down I can see a working version of Terminal where the box was, but because it's shutting down I can't access it.

Additionally, if I hit [esc] on startup I can access the root cli.  I tried to install mplayer using the following;

*apt-get install mplayer mplayer-fonts gnome-mplayer*

but it failed to retrieve any packages.  Needless to say I am lost.

It is a fairly old computer but I know next to nothing about hardware.

If this sounds like an issue anybody can tackle I'd welcome any ideas.

---

### Post by Vadi on 2008-12-08
Hi,

I think that your Ubuntu installation is unfortunately corrupted - most likely due to a bad CD.

I'd recommend burning another cd with Ubuntu, and reinstalling over the current one. Before you install, run the "disk integrity check" on the cd (it's an option after you put it in the cd drive and boot the computer) to make sure that the CD is OK.

---

