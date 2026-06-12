---
title: "Replacing text menus with icons or dropdowns"
date: 2009-02-28
forum: Desktop Environments
---

### Post by lduperval on 2009-02-28
Hi,

A few questions on GNOME (on Hardy):

[LIST]
[*]The standard menus (Applications/Places/System) take too much space on my panel at the top. How can I replace the text with icons only, to reduce real estate?
[*]Is there a way to revert the GNOME menu to their defaults?
[*]In XFCE, I could add a menu with a dropdown to my panel. Can I do this in GNOME?
[/LIST]

Thanks,

L

---

### Post by dbbolton on 2009-02-28
> **lduperval said:**
> Hi,

A few questions on GNOME (on Hardy):

[LIST]
[*]The standard menus (Applications/Places/System) take too much space on my panel at the top. How can I replace the text with icons only, to reduce real estate?
[*]Is there a way to revert the GNOME menu to their defaults?
[*]In XFCE, I could add a menu with a dropdown to my panel. Can I do this in GNOME?
[/LIST]

Thanks,

L
1. You can try replacing the Menubar applet with the simpler Menu applet. It will just be one button rather than Apps, Places, and system, but it will still have all the same entries. I don't know if you can get rid of all the icons, but you can get rid of most of them by adding this line to your current theme's gtkrc file (let me know if you need more explanation about this):
```
gtk-menu-images = 0
```

2. Go to system > Preferences > Main Menu. There is a "Revert" button in the lower right corner.

3. Not sure what you mean by menu with a dropdown. Can you explain, or post a screenshot of it?

---

### Post by lduperval on 2009-02-28
Thanks, I'll take a look at those options.

For #3, I would like to be able to create arbitrary dropdown menus like the "Applications," Places," and "System" menus in the GNOME menu. I know XFCE allowed you to do that by specifying (in an option) if your launcher was a real launcher or a menu.

L

---

### Post by dbbolton on 2009-02-28
> **lduperval said:**
> Thanks, I'll take a look at those options.

For #3, I would like to be able to create arbitrary dropdown menus like the "Applications," Places," and "System" menus in the GNOME menu. I know XFCE allowed you to do that by specifying (in an option) if your launcher was a real launcher or a menu.

L
I'm pretty sure that the only menu-like applets for gnome-panel are the Menubar and the Menu.

Just curious, why did you switch from Xfce to Gnome?

---

### Post by lduperval on 2009-02-28
Two reasons: laziness and integration. While Xfce had some nice features, I found that integration wasn't complete (2 years ago). So I moved to GNOME because the various pieces were better integrated. Plus, since it was the default with ubuntu, I had less work to do to set up my system as I wanted it. The xfce version required more manual tinkering on my part and I want to do less of that.

L

---

### Post by dbbolton on 2009-02-28
> **lduperval said:**
> Two reasons: laziness and integration. While Xfce had some nice features, I found that integration wasn't complete (2 years ago). So I moved to GNOME because the various pieces were better integrated. Plus, since it was the default with ubuntu, I had less work to do to set up my system as I wanted it. The xfce version required more manual tinkering on my part and I want to do less of that.

L
If you have a good bit of memory (like a gig or so), you could consider running xfce4-panel inside your Gnome session

---

### Post by NSDragon on 2009-02-28
> **lduperval said:**
> For #3, I would like to be able to create arbitrary dropdown menus like the "Applications," Places," and "System" menus in the GNOME menu. I know XFCE allowed you to do that by specifying (in an option) if your launcher was a real launcher or a menu.

There's an applet called drawer or something like it. Once you put it in your bar, you can open it and drag other launchers into it.

---

### Post by lduperval on 2009-03-01
The drawer does what I want, thanks.

L

---

