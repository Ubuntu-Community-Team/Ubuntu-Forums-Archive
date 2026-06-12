---
title: "Workspace switcher - how to get it back?"
date: 2006-01-15
forum: Desktop Environments
---

### Post by Kure on 2006-01-15
Hello,

I have a really lame question – how to get back the “workspace switcher” button / menu at the task bar in KDE?

I somehow managed to remove it and I can't find a way to restore it. I have 4 workspaces enabled, I can send a program to e.g. number 2, but I can't get there because I juts don't have the menu.

Right-clicking the task bar and choosing add to ... won't help as there is no such applet / application / ...

And again, sorry for such question, but its my a typical problem with Linux – I can install Gentoo and administer a server, but I can't find a stupid menu :???:

---

### Post by GeneralZod on 2006-01-15
This thing?

[img]http://etotheipiplusone.com/desktop-previewer.png[/img]

Add Applet -> Desktop Previewer and Pager.

---

### Post by Kure on 2006-01-15
Thank you for your reply.

The actual problem was a bit more complicated, the “kicker” wasn't able to load certain scripts, including the whole taskbar (I realized this after reboot, when I saw an error message). I guessed it was caused by incorrect installation of kde_xp theme.

Reinstalling of the kicker from aptitude solved the whole problem, because now I have something in the Add to panel -> Applet.

---

