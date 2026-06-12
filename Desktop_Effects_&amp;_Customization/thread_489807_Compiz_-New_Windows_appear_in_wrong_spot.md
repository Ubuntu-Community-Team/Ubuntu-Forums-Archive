---
title: "Compiz -New Windows appear in wrong spot"
date: 2007-07-01
forum: Desktop Effects &amp; Customization
---

### Post by LouisvilleLIP on 2007-07-01
I'm using Compiz Fusion.  Any new window, regardless of the app, places the title bar and menu bar above and behind my gnome menu bar (See attachment).  I can manually drag it down and it will snap into place, but it would be nice if it just went where it was supposed to go.  I keep messing with the settings in CompizConfig Settings Manager, but I can't seem to find the thing that will correct the problem.  Any suggestions?

---

### Post by ThrobbingBrain66 on 2007-07-01
In CCSM, click the Put plugin and click the Misc. Options tab.  Tick the 'Avoid Offscreen' box and see if that fixes it.  Alternatively, if that doesn't work, I've found that the gconf backend is significantly more stable and reliable than the flat-file backend at the present time.  The only drawback is that you lose a majority of your settings in the switch.

---

### Post by LouisvilleLIP on 2007-07-01
EDIT: It didn't work after all.  It's not a huge deal, I'd rather just move the windows for now, i don't want to risk breaking something else.

---

### Post by hyperair on 2007-07-02
Are you sure the gconf backend is more stable? I've tried it, and there are a few settings that will not stick. Only the flat-file backend works perfectly.

---

### Post by michaelzap on 2007-07-02
I've had window placement problems pretty consistently from Beryl to Compiz-Fusion. I had Beryl working bearably by choosing the "Center" placement method (instead of "Smart", which was more like "Insane"). When I switched to Compiz-Fusion windows were all over the place again, even using "Center". Then magically after a recent update they are working the same as they did under Beryl. I assume that they're working on this code and it will get better in the near future.

---

### Post by ThrobbingBrain66 on 2007-07-02
> **hyperair said:**
> Are you sure the gconf backend is more stable? I've tried it, and there are a few settings that will not stick. Only the flat-file backend works perfectly.

Gconf works almost perfectly for me.  When I was using the flat-file backend, I couldn't get any window shadows using gtk-window-decorator and many settings didn't stick.  Now that I use the gconf backend everything sticks except for window opacity settings.

---

### Post by hyperair on 2007-07-02
Did you enable the Inotify plugin? I reckon that one's essential for the settings to work with the flat-file backend.

---

### Post by ThrobbingBrain66 on 2007-07-02
I never knew what it was so I don't think I tried using it.  I'll try that though and let you know.

EDIT: After enabling the Inotify plugin, everything seems to be tip-tip, thanks for the hint.

---

### Post by hyperair on 2007-07-02
Good to hear ^^

---

