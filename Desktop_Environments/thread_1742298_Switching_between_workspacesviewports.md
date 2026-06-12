---
title: "Switching between workspaces/viewports"
date: 2011-04-28
forum: Desktop Environments
---

### Post by deludrien on 2011-04-28
[COLOR=#000000][FONT=Sans]Hi, I just switched to Natty today and I've noticed that when I switch between viewports/workspaces in Ubuntu Classic, my docks, notification-window-things (like for mail and chat) and my panels all move instead of just my windows, like they did in Maverick. Is there any way I can lock down these things so they don't move when I switch viewports?

EDIT: Even my wallpaper is moving!
[/FONT][/COLOR]

---

### Post by Copper Bezel on 2011-04-29
Are you running Compiz or Metacity/Mutter? The smooth slide that only affects "normal" windows is a behavior of the Compiz Desktop Wall. Under the Viewport Switching tab, the text box for non-sliding windows should look like 

```
type=Dock | type=Desktop | state=Sticky
```

---

### Post by deludrien on 2011-04-29
Thanks, that worked perfectly.

---

### Post by Copper Bezel on 2011-04-29
Excellent. = )

---

### Post by finwake on 2011-05-01
Thank you | Thank you | Thank you

---

