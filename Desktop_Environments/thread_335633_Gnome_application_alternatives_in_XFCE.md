---
title: "Gnome application alternatives in XFCE"
date: 2007-01-10
forum: Desktop Environments
---

### Post by zgoda on 2007-01-10
I recently installed Xubuntu on my wife's old laptop, since default Ubuntu was bit too sluggish on her machine. She seems to be happy with it, but there's always a "but...". ;) She misses some applications, that are part of Gnome desktop, for now her biggest problem is lack of graphical system logs viewer. What can you suggest?

---

### Post by happy-and-lost on 2007-01-10
The great thing about Linux is that you can build a sort of patchwork quilt-style environment consisting of the best bits of all the seperate software groups. For example, I currently use a hybrid Desktop which uses Gnome themes, panels and administrative apps, XFCE file manager, Openbox WM... you get the idea. You should be able to use the gnome system log viewer just fine with XFCE.

---

### Post by zgoda on 2007-01-10
> **happy-and-lost said:**
> The great thing about Linux is that you can build a sort of patchwork quilt-style environment consisting of the best bits of all the seperate software groups. For example, I currently use a hybrid Desktop which uses Gnome themes, panels and administrative apps, XFCE file manager, Openbox WM... you get the idea. You should be able to use the gnome system log viewer just fine with XFCE.

Yes, I knew it would be possible, but gnome-utils will install half of Gnome desktop as dependency... ;)
Anyway, will give a try.

---

### Post by BoneKracker on 2007-01-21
xfce4 has a nice terminal...

Why run a big, fat app when viewing (even tailing) log files is a function so intrinsic to linux itself.  In fact, you can do it on one of your spare vtt's very easily

press ctrl+alt+F<2 or whatever>
tail -f /var/log/<whatever>.log

all it takes to switch back and forth is a keypress

Also, if logs are important to her, you may want to look into replacing the default ubuntu syslog setup with syslog-ng or metalog which are much more configurable.

---

### Post by kerry_s on 2007-01-21
You can also use conky to put that kind of info right on the desktop and monitor all kinds of other stuff as well.

---

### Post by BoneKracker on 2007-01-21
My point was that if she switched to xfce4 from gnome to lighten the load, the best way to handle log viewing might be the use the getty's that are already running rather than loading up a fat xterm or other app (like some log-viewer or conky).

Of course, I realize there may be some specific functionality of the log viewer that she values enough to make it worth it.

---

### Post by kerry_s on 2007-01-21
Dude conky runs at a meager .18%, a freckin terminal runs more than that. Plus it can also be used in place of some of those much more demanding panel-app monitors.

---

### Post by BoneKracker on 2007-01-21
Wow.  I had no idea it was that lean.  That's about half what even a getty uses!
Assuming that's the actual load with it doing something, that would be a good alternative.

---

### Post by kerry_s on 2007-01-21
> **BoneKracker said:**
> Wow.  I had no idea it was that lean.  That's about half what even a getty uses!
Assuming that's the actual load with it doing something, that would be a good alternative.

Actual load? I have it running all the time, it uses .20 of cpu every 5sec then goes back to sleep. I have mine set to refresh every 5.0, but it can be set to what ever the user prefers.Here's a shot of it when it's using cpu->

---

