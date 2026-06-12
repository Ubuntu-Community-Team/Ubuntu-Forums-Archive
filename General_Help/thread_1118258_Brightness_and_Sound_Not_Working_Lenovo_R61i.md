---
title: "Brightness and Sound Not Working Lenovo R61i"
date: 2009-04-06
forum: General Help
---

### Post by eriol1213 on 2009-04-06
Going from the default 8.1 CD installation to the fully updated version, my brightness keys (Fn+Home for brightness up) and (Fn+End for brightness down) stopped functioning.

The brightness of the screen just stays at a constant level no matter how I try to adjust it. The laptop detects if the keys are being pressed, in fact when I try to press it, it adjusts the brightness slider that pops up. It's just that this has no effect on the actual brightness.

The brightness applet that you can add to the panel also doesn't work.

I've reinstalled Ubuntu 8.1 several times on my laptop and every time I upgrade, it always has this problem.

Any suggestions?

**The sound works, actually. The sound not working was another issue that I soon fixed.**

---

### Post by Brucevdk on 2009-04-17
I'm facing the brightness issue using Intrepid on a ThinkPad X61t. See [this search on Launchpad](https://bugs.launchpad.net/ubuntu/+bugs?field.searchtext=BACKLIGHT_CONTROL&orderby=-importance&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=) for a number of relevant issues, [this report in particular](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313231) might interest you. 


The workaround I've been using is having the following command execute on startup (though I'm trying [this](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/313231/comments/6) next):

```

xrandr --output LVDS --set BACKLIGHT_CONTROL native

```

---

