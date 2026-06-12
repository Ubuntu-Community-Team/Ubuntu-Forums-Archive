---
title: "xmonad+unity-2d+multimon  refresh problems"
date: 2011-11-17
forum: Desktop Environments
---

### Post by boghead on 2011-11-17
Using two monitors under xmonad using the unity-2d launcher and panel, sometimes when I change workspaces on one screen whatever was on my other screen disappears -- the desktop draws over whatever was there.  If I switch back to the previous screen, my windows will draw again if I cycle through them.

Is there a bug here?  Is there some way to prevent the desktop from drawing over my windows?  Is there some way I could force the windows on the inactive screen to redraw when I switch workspaces?

I am not sure if this is a problem with multiple monitors, a problem with xmonad, or a problem using xmonad with unity.  Please let me know if I would be better served asking about this somewhere else.

---

### Post by TheOtherShoe on 2012-01-31
I have the same problem.  Has anyone come across a solution for this?

---

### Post by TheOtherShoe on 2012-01-31
I think that I may have fixed the problem by configuring Nautilus to disable desktop icons.  To do that in Oneiric you can run this command:

```
gsettings set org.gnome.desktop.background show-desktop-icons false
```

In older versions of Ubuntu where Nautilus is configured with gconf, use this command:

```
gconftool -t bool /apps/nautilus/preferences/show_desktop -s false
```

---

