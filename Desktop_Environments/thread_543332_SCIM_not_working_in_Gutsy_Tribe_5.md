---
title: "SCIM not working in Gutsy Tribe 5"
date: 2007-09-05
forum: Desktop Environments
---

### Post by dchart on 2007-09-05
I have Gutsy Tribe 5 (Gnome) installed on my new 20" Metallic iMac. Most of it works fine, but Feisty doesn't, so I need to stick with this version.

I have installed, from the repositories, scim (comes by default) and anthy/scim-anthy (for Japanese input). My home directory is from my previous install, on a different machine, which was running 6.10. Over there, scim-anthy worked fine.

Scim is not working. Hotkeys don't activate it, and the right-click Input Methods menu doesn't work, either. The configuration panel works, and I can start it from the command line, although not make it actually do anything.

Any suggestions gratefully received; I'm not sure whether this is a bug or my misconfiguration.

---

### Post by dchart on 2007-09-05
Following up to myself... This seems to be an environment problem, because I had everything working briefly. Unfortunately, when I thought I had fixed the environment to be like that automatically, I hadn't, and I've not been able to get things working again. :(

Edit: Rather than clutter up with posts, I'll just add information. I can't get the necessary environment variables to "stick", or, indeed, to take effect outside a terminal session. However, XMODIFIERS="@im=SCIM" and GTK_IM_MODULE="scim" produce a working system for anything launched from within the terminal. Putting them in bashrc makes my workaround fairly simple. Still, it should be possible to set them globally at the beginning of each session. But where?

Edit: &#12391;&#12365;&#12383;&#12290;That's Japanese for "done it". I ended up editing /etc/environment to put the necessary environment variables in, which I don't generally like doing; there must be a local alternative, surely. Anyway, it is now working for me.

---

