---
title: "Gnome alt-tab and dragging between desktops"
date: 2007-03-08
forum: Desktop Environments
---

### Post by actuary286 on 2007-03-08
I recently switched from Xubuntu to Ubuntu when I got a new computer and love Gnome, but miss a few of XFCE's functions:

[LIST=1]
[*]Is it possible to alt-tab between all windows, regardless of desktop? I realize that I can use ctrl-alt-left arrow/right arrow to move between desktops, but that takes two hands and alt-tab takes one.
[*]Can you drag windows between workspaces? In XFCE you can any window on the desktop and drag it to the very left or right edge of the screen and it will pop over to the next desktop automatically.
[/LIST]

Thanks.

---

### Post by SuSUntu on 2007-03-08
I know this isn't the ideal answer (I'm just too lazy to switch to my Gnome / Metacity setup right now), but I **think**:

- the alt-tab functionality MAY be available in the Preferences>Windows settings.
- the drag-window-to-virtual-desktop feature can be added via a 3rd-party app called [BrightSide]("http://en.wikipedia.org/wiki/Brightside")

You can get some additional functionality from DevilsPie.

Now for my opinion:

Add XFWM4 as your windows manager and get the functionality back that you had with XFCE. Not only do you get a better windows manager with more / better features, you also lose the Metacity animations (which is a good thing). Set AIGLX in Xorg.conf and then you've got nice, smooth transparent window functionality, too.

See this post for simple instructions if needed:
[http://ubuntuforums.org/showthread.php?t=88393](http://ubuntuforums.org/showthread.php?t=88393)

I skipped the section which describes how to get the XFWM configuration utility registered with Preferences >Windows in Gnome (I just created a regular shortcut to the utility and placed it in the Gnome menu), so I can't vouch for that. However, everything else works perfectly.

---

### Post by actuary286 on 2007-03-08
Thanks, this works perfectly and gives me everything I need.

---

