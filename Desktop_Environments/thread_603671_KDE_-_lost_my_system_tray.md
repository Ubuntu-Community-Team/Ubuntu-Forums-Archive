---
title: "KDE - lost my system tray"
date: 2007-11-05
forum: Desktop Environments
---

### Post by skullmunky on 2007-11-05
ok - i feel kind of dumb asking this - but it's driving me nuts for days ... my KDE System Tray (the one with the little minimized icons for KMix, Amarok, etc...) has disappeared, and I really can't find it again!  

In "Add to Panel" I don't have anything called "System Tray" or "Notification Area" at all.  And, I think it's still running, just invisible - it keeps swallowing apps when I quit them, so for example Amarok is now unquittable without resorting to the terminal and I must now listen to music all the time ... oh the horror .. :) 

anyway, thanks for any suggestions - i'm thinking there ought to be some command-line way to just relaunch it, like kicker, etc?

---

### Post by der_joachim on 2007-11-05
> **skullmunky said:**
> ok - i feel kind of dumb asking this - but it's driving me nuts for days ... my KDE System Tray (the one with the little minimized icons for KMix, Amarok, etc...) has disappeared, and I really can't find it again!  

In "Add to Panel" I don't have anything called "System Tray" or "Notification Area" at all.  And, I think it's still running, just invisible - it keeps swallowing apps when I quit them, so for example Amarok is now unquittable without resorting to the terminal and I must now listen to music all the time ... oh the horror .. :) 

anyway, thanks for any suggestions - i'm thinking there ought to be some command-line way to just relaunch it, like kicker, etc?

I've had this problem numerous times. Every time, I had misconfigured something in my KDE panel. Most of the time it had something to do with autohiding and autoraising the panel when the mouse pointer hits the wrong screen edge or corner. :(

Anyhoo, here's how to reset your panel config:
- If not installed already, install kcontrol. You get the good ol'fashioned KDE control center instead of Kubuntu's less-than-complete system settings menu thingy.
- Open kcontrol.
- Desktop >> Panels
- Either fiddle with the settings (you'll want to try the settings under the tab labeled *Hiding*), or click the *Defaults* button.
- Click *Apply*.

Hope this helps

---

### Post by skullmunky on 2007-11-05
oh, wow! thanks!

turns out the system tray hadn't disappeared - I had a WHOLE OTHER PANEL that had disappeared!

I tried to set up my panels with one at the top for shortcuts and one at the bottom for the taskbar - but somewhere along the line forgot about the "Main Panel" which had auto-hiding on and so was always hidden behind one of the other two.   joy!  now I can quit amarok and stop listening to french electro.

---

