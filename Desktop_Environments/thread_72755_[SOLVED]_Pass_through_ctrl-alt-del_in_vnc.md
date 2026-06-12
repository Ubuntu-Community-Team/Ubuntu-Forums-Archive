---
title: "[SOLVED] Pass through ctrl-alt-del in vnc?"
date: 2005-10-07
forum: Desktop Environments
---

### Post by MikeyXX on 2005-10-07
So I'm running VNCVIEWER from KDE. When I hit the ctrl-alt-del to log into the xp that I'm vnc-ing to, it brings up the KDE loggout screen. I've been to the \etc\inittab and put a # infront of ca::ctrlaltdel: but it didn't work.

F8 doesn't work to offer the keys like in the Windows version of VNC

---

### Post by MikeyXX on 2005-10-07
Damn, F8 did bring up the list of keys to send. I don't know why it wouldn't for so long. Ok, so it'll work. I'm still curious on why #-ing out that line didn't stop the action of ctrl-alt-del on the shell.

---

### Post by mlomker on 2005-10-07
>  I'm still curious on why #-ing out that line didn't stop the action of ctrl-alt-del on the shell.

That just disables a shutdown when at a terminal prompt.  KDE hotkeys are configured in the Control Center under Regional & Accessibility, Keyboard Shortcuts.  The one that you are looking for is under Desktop, Log Out.

---

### Post by MikeyXX on 2005-10-08
Great, I'll have a peak there. Thanks!

---

