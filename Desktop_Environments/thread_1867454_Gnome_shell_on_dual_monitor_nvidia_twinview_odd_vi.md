---
title: "Gnome shell on dual monitor nvidia twinview: odd virtual workspace issue"
date: 2011-10-23
forum: Desktop Environments
---

### Post by sgarman on 2011-10-23
Hello,

I have an unusual issue with GNOME Shell 3.2 on my Ubuntu Oneiric system.

I have a dual monitor setup using the proprietary NVIDIA drivers in twinview mode. 

The screen spans both monitors, but the GNOME shell bar along the top only spans one of the monitors. If I hit the upper-left corner of either screen, the dock thing appears - it is positioned on the left side of the first screen (basically in the middle of the dual-screen space).

I didn't think this would be a problem, but now I'm noticing another possible effect from it. Windows I place in the second monitor's space remain in view when I switch workspaces, as if I had enabled the "show on all workspaces" window manager feature. I can drag the window back into the primary monitor's area and it correctly disappears when I move to another workspace. 

Can anyone tell me how to fix this? I'm thinking if GNOME shell knew to extend the top bar across both monitors, that would fix the issue.

This is a weird issue so I hope I'm explaining it correctly.

Thanks,

Scott

---

### Post by wstout on 2011-10-25
I had the same issue with GNOME shell. If nothing has changed in 3.2 this will fix things for you:

[http://gregcor.com/2011/05/07/fix-dual-monitors-in-gnome-3-aka-my-workspaces-are-broken/](http://gregcor.com/2011/05/07/fix-dual-monitors-in-gnome-3-aka-my-workspaces-are-broken/)

What you experienced is desired behavior by the GNOME devs.

---

### Post by sgarman on 2011-10-25
That's exactly the info I was looking for, thank you!

Scott

---

