---
title: "Any known broken updates in 5.10 recently?"
date: 2006-06-13
forum: Desktop Environments
---

### Post by agenkin on 2006-06-13
Greetings:

Short version of the question: have there been any known problems with Ubuntu/Kubuntu package updates recently, mostly Xorg/QT/KDE-related?

Two of Kubuntu workstations recently started acting up.  Both after a reboot, and both have "apt-get update; apt-get upgrade" run via a daily cron script, so I am thinking that a recent package update could have caused the problem.

On my wife's workstation, KDE would no longer start: startkde segfaults.  If "startkde" is replaced with "xterm" in her ~/.xsession, kdm brings the xterm just fine, but some commands (like firefox, startkde, and a few more) segfault when launched from that xterm.  I examinted the environment for anything strange, reset her .Xauthority file, ~/.kde and ~/.kderc, and made sure that her shell dot-files have not been modified recently.  For the life of me I cannot figure this out.  My account on the same computer launches KDE just fine.

My workstation was just rebooted after a while, and when I launched KDE, it came up with some errors (some applets did not launch, such as the KDE system tray).

---

