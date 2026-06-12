---
title: "Troubles after uninstalling beryl"
date: 2007-05-01
forum: Desktop Effects &amp; Customization
---

### Post by dolik.rce on 2007-05-01
I've instaled beryl just to try it, everything was working smooth without problems. The troubles started after removing beryl - the window manager doesn't work properly. Actually it doesn't work at all :( 
I've found this so far:
[LIST]
[*]after logging in, there are no buttons on the top of the windows
[*]if i install  beryl back again, just start it, set it to work with my usual window manager and shut it off, everything works OK until logging out
[*]now, even with installed beryl, the window manager won't start until starting beryl
[*]if I try to enter window manager settings, it says that the "setting won't work with current window manager (unknown)" and doesn't even show the settings window
[/LIST]
Can somebody tell me how to get beryl off my computer properly?
I've tried removing it with Synaptics as well as from terminal, always with same effect. I'm using Xubuntu 7.04...
Thanx for any hint or help...

---

### Post by scanez on 2007-05-01
Uninstall Beryl, then log into gnome and try running

metacity --replace

from a terminal. Assuming this works, next time you log into gnome again metacity should start automatically. Let us know if not!

---

### Post by dolik.rce on 2007-05-01
Thanks for help altough I haven't really used it. 
I've just tried to uninstall and start a new session in Gnome. There was everything Ok under Gnome and even after switching to Xfce everything is working again.
BTW I've already tried that trick with replacing metacity before, but I think (but I'm not sure) that metacity is only in gnome. In Xfce it did nothing...

I just wonder why it started to work after switching to gnome... :confused:

---

