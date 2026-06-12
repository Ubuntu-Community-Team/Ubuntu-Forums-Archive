---
title: "multiple desktops"
date: 2009-07-18
forum: Desktop Environments
---

### Post by fusi.eon on 2009-07-18
i've been using linux [kubuntu] for quite a while now. 

the other day i tried opensolaris live cd, and in the multiple desktop feature, i noticed that there is a difference in what kubuntu offers.

for example, if on desktop 1, i've firefox open. and if i click on desktop 2, the taskbar clears [in opensolaris] and if i click on desktop 1, only then will it show firefox in the taskbar.. while for kubuntu, even if i click on desktop 2, it will show firefox open. is there any way to clear the task bar like it does in opensolaris? 

sorry if this is a stupid question. but thanks!

---

### Post by ibutho on 2009-07-18
Right click on the panel and in the panel settings untick "Show windows from all desktops". This maybe a bit different if using KDE4.

---

### Post by Zorael on 2009-07-18
Yep, the KDE way is to similarly right click the task manager and enter its settings, then check *Only show windows from the current desktop*. If it's hard to right-click it (as in, you have task entries covering it), unlock widgets, hit the cashew on the panel, and then right-click the task manager again.

---

### Post by fusi.eon on 2009-07-18
> **ibutho said:**
> Right click on the panel and in the panel settings untick "Show windows from all desktops". This maybe a bit different if using KDE.

you're right. there's no such option.

now what?

---

### Post by fusi.eon on 2009-07-18
> **Zorael said:**
> Yep, the KDE way is to similarly right click the task manager and enter its settings, then check *Only show windows from the current desktop*. If it's hard to right-click it (as in, you have task entries covering it), unlock widgets, hit the cashew on the panel, and then right-click the task manager again.

thanks! that worked!

what does this option mean 'Only show windows from the current screen'? what's the difference between screen and desktop?

---

### Post by Zorael on 2009-07-18
I guess the names can be a bit confusing.
[list][*]**"Desktops"** are what you get when you split up your workspace on the same monitor, to use with a pager or as a cube.
[*]**"Screens"** are separate monitors that share the currently running session (TwinView, Xinerama). In turn they can share desktops or have their own set.
[*]**"Displays"** are separate X sessions that cannot talk to eachother (do not share apps). In turn, they can (obviously) have multiple screens, and by extension, multiple desktops.[/list]
So you always have at least one of each. Even in a usercase where there's no monitor attached (to instead be manipulated remotely), I'd argue that there's still a screen -- just not a monitor it's assigned to. Semantics, though.

---

### Post by fusi.eon on 2009-07-18
ahh..thanks!

---

