---
title: "Alt+F1 keyboard shortcut to Kickoff (application launcher) does not work"
date: 2012-03-23
forum: Desktop Environments
---

### Post by brm on 2012-03-23
This is a problem I have had for several months. IIRC, it first began while I was using Kubuntu natty, but has persisted through oneiric and is still there with the precise beta.

The problem is simply that the Alt-F1 keyboard combination does not work on this one x64 instance. It works with other machines running Kubuntu.

When I right click on the KickOff icon, it shows no keyboard shortcut. If I try to enter Alt-F1, an error dialog box pops up stating:

Conflict with Registered Global Shortcut - Plasma Desktop Shell

The shortcut 'Alt+F1' conflicts with the following key combination:
Shortcut 'Alt+F1' in Application Plasma Desktop Shell for action Activate Application Launcher Widget

And when I check |System Settings |Global Shortcuts |Plasma Desktop Shell, the shortcut does appear there. The config file entry appears to be:

.kde/share/config/kglobalshortcutsrc:activate widget 31=Alt+F1,Alt+F1,Activate Application Launcher Widget

So, I have two questions;
1) What is my best immediate work-around? Presumbably to overwrite the Global Shortcut, as the error dialog box invites me to do.
2) I see this as a bug, um, er, unexpected feature. Where would it be most useful to report it?: *buntu launchpad.net bug database? the KDE bug database?

Thanks in advance for any assistance.

---

### Post by kio_http on 2012-04-10
Seems like some sort of corrupted config or something. Try resetting KDE to defaults if you don't mind losing your settings.

---

