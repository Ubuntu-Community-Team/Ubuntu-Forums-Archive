---
title: "Beryl control panel MIA"
date: 2007-01-29
forum: Desktop Environments
---

### Post by irish_flu on 2007-01-29
Hey folks,

OK maybe I'm losing it, but I could have sworn that before I upgraded to this version of Beryl (0.2.0 Beta2) there was a "Beryl Settings Manager" Under the System --> Preferences menu.  Am I nuts?

There is an Emerald Control Panel there, but no Beryl Settings Manager.  I've heard some people say that they have a Beryl icon in their gnome-panel's Notification Area, but I've not seen that in either this version of Beryl, nor the last one I ran.

Beryl is running, though (it performs great, actually); all my whiz-bang eye candy is there, and I can see a beryl process running in the System Monitor.  Restarting X doesn't make a difference.  It hasn't seemed unstable in any other way, I've only experienced beryl-core crashing once.

Of course the answer is "hey, it's version 0.2.0 and has 'beta' right in the name!".  :D 

Still, I'd appreciate any thoughts on how I might access the Settings Manager.

I have Beryl set to start up when Gnome starts.

Thanks in advance,
Irish_Flu

---

### Post by Waappu on 2007-01-29
> **irish_flu said:**
> Hey folks,

OK maybe I'm losing it, but I could have sworn that before I upgraded to this version of Beryl (0.2.0 Beta2) there was a "Beryl Settings Manager" Under the System --> Preferences menu.  Am I nuts?

Hi

Setting manager not exists anymore there. I don't know why.

See if you can find setting manager from Applications->System Tools.
If you start Beryl with command ```
beryl-manager
``` does red gem appear to notification area?

---

### Post by irish_flu on 2007-01-29
SWEET, that worked!  I'll just run "beryl-manager" at startup.

Many thanks, Waappu!

---

### Post by Waappu on 2007-01-29
Hi

=)

I think you can start setting manager also from terminal by ```
beryl-settings
```or create launcher. If you don't like that icon in your notification area

---

