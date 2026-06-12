---
title: "My GNOME isn't working, but only mine."
date: 2011-02-17
forum: Desktop Environments
---

### Post by abelundercity on 2011-02-17
Doing my best to omit no details:

I was using the Second Life Imprudence viewer under GNOME in Ubuntu 9.10.  After closing my session I tried opening the Chrome browser, which didn't open.  I tried Firefox next, and after a few turns of activity that also failed to open.  Then I tried opening Chess, which also failed to open.  Not knowing what else to do, I restarted the machine.  I had to do it via the power button on my case, as GNOME was no longer taking commands.

Upon restart and login, I was faced with my wallpaper, my mouse pointer - which moved normally - and nothing else.  No panels, no icons, nothing.  A little too late, I remembered that I had GNOME set to run any processes that were running in the last session, and my guess is this has something to do with the problem.

My wife has her own account on the machine, so I logged into hers and found everything working normally.

My session won't restore, not in regular GNOME or in failsafe mode. Xterm still comes up but I'm at a loss as to where to go from there.

If anyone has any input as to how I can get my side of the computer back, I would greatly appreciate it.  Thank you.

---

### Post by anglican on 2011-02-18
> **abelundercity said:**
> Doing my best to omit no details:

I was using the Second Life Imprudence viewer under GNOME in Ubuntu 9.10.  After closing my session I tried opening the Chrome browser, which didn't open.  I tried Firefox next, and after a few turns of activity that also failed to open.  Then I tried opening Chess, which also failed to open.  Not knowing what else to do, I restarted the machine.  I had to do it via the power button on my case, as GNOME was no longer taking commands.

Upon restart and login, I was faced with my wallpaper, my mouse pointer - which moved normally - and nothing else.  No panels, no icons, nothing.  A little too late, I remembered that I had GNOME set to run any processes that were running in the last session, and my guess is this has something to do with the problem.

My wife has her own account on the machine, so I logged into hers and found everything working normally.

My session won't restore, not in regular GNOME or in failsafe mode. Xterm still comes up but I'm at a loss as to where to go from there.

If anyone has any input as to how I can get my side of the computer back, I would greatly appreciate it.  Thank you.Try typing [ALT][F2] and running nautilus - this problem is most usually caused by nautilus crashing.

H

---

### Post by abelundercity on 2011-02-18
Alt-F2 garners no response.  So far the only reaction I've been able to get is from CTRL-ALT-DEL, which kicks me back to the login screen.

---

### Post by anglican on 2011-02-18
> **abelundercity said:**
> Alt-F2 garners no response.  So far the only reaction I've been able to get is from CTRL-ALT-DEL, which kicks me back to the login screen.Wow, no [ALT][F2] - I've never seen that! Can you get a console with [CTRL][ALT][F1]? If so you could try to run something like:
```
xterm -display :0
```which may open a terminal then run nautilus from that terminal ([CTRL][ALT][F8] gets you back to your desktop). Basically if nautilus isn't running you get no desktop.

H

Oh, I've just noticed in your original post that xterm is already coming up. Can't you run nautilus there?

---

### Post by abelundercity on 2011-02-18
To be entirely honest, I didn't know to try.  I'm a fairly dab hand with the GIMP and related applications, but not so much with the under-the-hood stuff.

I'll give it a try when I get back home.  Thank you so much for your help.  I'll probably be posting an update on this in about eight hours or so.

---

### Post by Copper Bezel on 2011-02-18
> Wow, no [ALT][F2] - I've never seen that! Can you get a console with [CTRL][ALT][F1]? If so you could try to run something like:

Alt+F2 is captured by the Gnome Panel, not Metacity or Compiz. No panel, no Alt+F2. It doesn't matter, though, because there's nothing Alt+F2 can do that XTerm can't.

Do you have a keyboard shortcut for System Monitor? (Alternately, does anyone know what the console-based System Monitor equivalent is?)

Otherwise, try gnome-session-properties from XTerm. 

If no (other) graphical apps will run and we can't get a text system monitor running so you know what to kill, we'll have to figure out where your session is saved and kill that file from xterm (or Ctrl+Alt+F1 console, if it comes to that.)

---

### Post by abelundercity on 2011-02-18
Just "gnome-session-properties" at the prompt?

Or, that said, is there a way to simply restore the system defaults?

---

### Post by abelundercity on 2011-02-19
OK, I managed to fix it, though I suspect it was taking the long way around the barn.  When Copper Bezel mentioned other graphic interfaces, it gave me the idea to try installing KDE, and lo and behold it worked.  I changed my session settings so that rather than continuing processes from previous sessions it would only start processes that I had specifically designated, and that carried over back into GNOME as well.

Thanks for the help!

---

