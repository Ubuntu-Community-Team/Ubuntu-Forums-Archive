---
title: "Mouse Wheel To Change Workspaces on Unity Without CCSM?"
date: 2014-09-29
forum: Desktop Environments
---

### Post by buzzingrobot on 2014-09-29
Anyone know of a way to change workspaces with the mouse wheel on Unity without installing CCSM?

That's all I use it for, but Compiz is grabbing around 300 MiB of memory. I have lots of RAM, but it just seems a more efficient way ought to be available.

---

### Post by mcduck on 2014-09-29
Installing CCSM won't have any effect on Compiz memory usage, it's just a tool for configuring Compiz settings. (And of course you are already running Compiz itself since it's the default window manager in Ubuntu and required by the Unity desktop).

---

### Post by buzzingrobot on 2014-09-29
> **mcduck said:**
> Installing CCSM won't have any effect on Compiz memory usage, it's just a tool for configuring Compiz settings. (And of course you are already running Compiz itself since it's the default window manager in Ubuntu and required by the Unity desktop).

Yeah, I'm sure that's correct. Should have thought of that.

Still, I'm used to seeing it at 90-100 MiB, not more than 300. That's a lot to pay for changing a workspace.

There are jury-rigged gizmos that map keystrokes to mouse actions, but they don't know when the cursor is over a window versus over the desktop, so they eleminate wheel scrolling altogether except for changing workspaces.

---

### Post by mcduck on 2014-09-29
Did you turn on some additional plugin in CCSM? If not, then just changing settings on already-enabled plugins, especially for as simple thing as this, definitely shouldn't have any noticeable effect on memory usage. (And it most certainly would be smaller than what running any additional software to emulate keypresses would cause)

How are you checking how much Compiz is using? And have you tried logging out & back again (or restarting Unity/Compiz) after you made the changes?

---

### Post by buzzingrobot on 2014-09-29
Checking in System Monitor. I'll assume it's an anomaly of some kind; I'll see what happens. I did install CrashPlan (the backup service) last night. Perhaps there's a connection. CrashPlan requires OpenJDK which also gobbles 300+ MiB, so I'll be cancelling and removing it.

All I do with CCSM is set Button 5 and Button 4 to Next and Previous workspace in Viewport Switcher.  

This functionality seems to be implemented via the window manager where it does exist:  Compiz, KDE, XFCE, extensions in Gnome Shell, etc. I'd like to find a universal approach that would work regardless of window manager.

---

### Post by mcduck on 2014-09-29
If you want a lightweight option, then you need to configure it directly in whatever window manager you are using. Any way of trying to configure such setting for various different window managers would mean running external program (and therefore would result in using more resources).

---

### Post by mc4man on 2014-09-29
'scroll on desktop' is a compz deal & really doesn't consume much mem.  Here compiz use about 70 MiB & switching ws's with sod doesn't add much if any.
Ex. - 
```
07:35:10 PM   UID       PID  minflt/s  majflt/s     VSZ    RSS   %MEM  Command
07:35:12 PM  1000      2007      0.00      0.00 1422972  67548   0.83  compiz
.... a lot of ws changing...
07:36:10 PM  1000      2007      0.00      0.00 1423084  67572   0.84  compiz

```
What does increase compiz's mem use is one of it's plugins - unity (Dash, launcher, panel, scopes, ect.

Though here with plenty to spare I'm all for as much mem use as possible, the more the better (excluding leaks..

---

### Post by buzzingrobot on 2014-09-29
The jump from around 90 to over 300 megs for Compiz wasn't related to enabling the scroll. The scroll's enabled as soon as I install CCSM. I'm not particularly concerned about lighweight options, although I am curious about that spike in memory use.

I'm just looking for the same functionality without the dependency on Compiz or any other window manager, something usable when the window manager doesn't provide it.

---

### Post by CantankRus on 2014-09-30
I like to use easystroke for a lot of window manager actions.
Binding gestures to ctrl+alt+right and ctrl+alt+left works in both metacity and compiz.
Other gestures can be configured using wmctrl and/or scripts.

---

### Post by vasa1 on 2014-09-30
> **buzzingrobot said:**
> ...

I'm just looking for the same functionality without the dependency on Compiz or any other window manager, something usable when the window manager doesn't provide it.I very much doubt that's possible. From what I've read, only the window manager handles desktop switching (or pagers). I hope I'm wrong.

---

### Post by mcduck on 2014-09-30
You could maybe get some kind of hack together using [wmctrl]("http://www.freedesktop.org/wiki/Software/wmctrl/"), of course the window manager must be one of the supported ones, and must also have virtual desktops, and you'll still need some way to detect if the mouse is over desktop or smoe other window (there probably is some way to script that, for example [xwininfo]("http://linux.die.net/man/1/xwininfo") is able to tell you the name of the window your mouse is over, so you could use something like that to check if the mouse cursor is over desktop window or X root window...  ).

...in the end it's probably easier to just stick with window managers that already support mouse wheel scrolling to switch desktops. MOst of the common ones do that anyway. :D

---

### Post by buzzingrobot on 2014-09-30
I'll look at wmctrl and easystroke again.  It's the bit about detecting when the mouse is over the desktop or not that was the sticking point. (Hadn't looked at xwininfo, so thanks.)

Yep, most windows managers implement this in some fashion. I'm just stubborn.:)

---

