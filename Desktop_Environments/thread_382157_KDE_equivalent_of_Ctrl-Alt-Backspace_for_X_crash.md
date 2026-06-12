---
title: "KDE equivalent of Ctrl-Alt-Backspace for X crash?"
date: 2007-03-11
forum: Desktop Environments
---

### Post by kundalinikat on 2007-03-11
Hey I'm running Dapper Ubuntu with the kubuntu package installed and started to use the Kubuntu environment instead of GNOME. Sometimes it will crash and Ctrl-Alt-Backspace does not restart X as it does in GNOME. Is there some way I can make Ctrl-Alt-Backspace work with KDE, or is there another key combination that will do the trick? (When it crashes the mouse cursor can move but I cannot interact in any other way.)
Thanks for your time, this community is great.

---

### Post by john.nicholls on 2007-03-11
Ctrl-Alt-Backspace SHOULD work in KDE the same way it works in Gnome. Sorry, but I don't know what to suggest, except that when KDE is working, you try Ctrl-Alt-Backspace to prove that it works then.

---

### Post by bernied on 2007-03-11
Ctrl-Alt-Backspace does work in KDE, it is operating on the X-server which is shared by both gnome and kde. If it is not working then X has crashed and is unable to get the signal.

Can you get a terminal using Ctrl-Alt-F1 (or F2 or F3, etc)?
If you can, then you can login and
```
sudo /etc/init.d/kdm restart
```If this does nothing, try replacing kdm with gdm (this is your display manager, I don't know if you are using gdm or kdm).

To get back to your (crashed) X-session, use Ctrl-Alt-F7.

---

