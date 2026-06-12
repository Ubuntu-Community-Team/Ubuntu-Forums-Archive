---
title: "date in top bar is not perfectly centered because of the dock"
date: 2019-03-03
forum: Desktop Environments
---

### Post by pippero98 on 2019-03-03
Hi everyone, I recently updated to 18.04 and so I moved to GNOME.
The problem is that the date in top bar is not centered, but I discovered that it starts being perfectly centered when the option to automatically hide the dock is active. With this option the date is centered even when the dock is displayed, so I don't understand why it doesn't work like that when the dock is set up to always be visibile.
I have attached two screenshot for comparison, hope someone can help me.

---

### Post by Dennis N on 2019-03-03
> **pippero98 said:**
> Hi everyone, I recently updated to 18.04 and so I moved to GNOME.
The problem is that the date in top bar is not centered, but I discovered that it starts being perfectly centered when the option to automatically hide the dock is active. With this option the date is centered even when the dock is displayed, so I don't understand why it doesn't work like that when the dock is set up to always be visibile.
I have attached two screenshot for comparison, hope someone can help me.

Interesting question. With autohide off, and dock always visible, the full screen window will be narrower than your monitor's display. So the date/time display moves to be centered over the reduced full-screen window.

---

### Post by vanadium on 2019-03-04
Indeed, Ubuntu changed the position of the clock in 18.04 so it would be centered over your available workspace (minus the dock). The need of this is most seen on a maximized window with a title bar. With the clock centered over the display, it would not center-align with a title of a maximized window without the correction (as was the case in 17.10).

Thus, with autohide: clock is centered over the entire display width
without autohide: clock is shifted to the right to center over the workspace (=display minus the dock).

---

### Post by pippero98 on 2019-03-04
> **vanadium said:**
> Indeed, Ubuntu changed the position of the clock in 18.04 so it would be centered over your available workspace (minus the dock). The need of this is most seen on a maximized window with a title bar. With the clock centered over the display, it would not center-align with a title of a maximized window without the correction (as was the case in 17.10).

Thus, with autohide: clock is centered over the entire display width
without autohide: clock is shifted to the right to center over the workspace (=display minus the dock).

thanks, I didn't think about the align with the window title! I guess the only way I have to make it look prettier is to edit the wallpaper so it looks aligned to the workspace center...

---

