---
title: "Gnome 3 Shell workspace scrolling not behaving like before"
date: 2014-06-03
forum: Desktop Environments
---

### Post by Ck.asdf on 2014-06-03
I am using Gnome Shell 3.10.4 on my desktop (specs listed in signature).  Before fresh-installing u14.04, I had 12.04 installed, though I'm not sure what version of Gnome Shell.

In the previous installation, when I press [Super] or move to "Activities" to see the activities preview and side-bar of workspaces, if I used the mouse scrollwheel above a program thumbnail, it would zoom in on the program so I could get a closer look at it.  If I used the scrollwheel over the side-bar, it would scroll through the workspaces.

However, now the current behavior is to scroll through workspaces regardless of mouse position.

My laptop, still on u12.10 (will be upgrading soon), has Gnome Shell 3.6.3.1, and my expected behavior (of zooming program thumbnails) works here.

Has something changed in the version, or perhaps an extension been installed?  How would I check what extensions are in use if that were the case? 

Thanks!

---

### Post by buzzingrobot on 2014-06-04
Tweak Tool will show you what extensions are installed.

If it's not installed, the package is: "gnome-tweak-tool".

---

### Post by Ck.asdf on 2014-06-04
Thanks for your reply.  I opened gnome-tweak-tool on my laptop and within it are several primary options, one of which is called "Shell Extensions," though there were no extensions listed there.  There were also no settings in any of the other options referencing this scroll/zoom behavior.

I then looked at gnome-tweak-tool on my desktop, which has just "Extensions" in its list of options, and it has several, though none of those reference the feature either.  Thoughts for anyone who has used it from version 3.6 to current?

---

### Post by buzzingrobot on 2014-06-04
The workspace scrolling behavior here on Gnome 3.10 is the same as you describe, i.e. it rolls through the available workspaces.  I don't recall the earlier behavior.

---

### Post by Ck.asdf on 2014-06-04
After further review, I found the following:

```

2013-02-20        workspace: Remove zooming of window previews        Florian Müllner        1        -200/+2
Using the scroll wheel to switch workspaces makes sense, but it is currently only supported on the workspace switcher, as it conflicts with window zooming in the picker. As changing workspaces is far more useful than the zoom feature, remove the latter in order to "free" the scroll wheel for workspace switching.

```
Source: [https://git.gnome.org/browse/gnome-shell/commit/?id=0e1221561427b84152887e8883b610be92f0ad98](https://git.gnome.org/browse/gnome-shell/commit/?id=0e1221561427b84152887e8883b610be92f0ad98)
Commit hash: 0e1221561427b84152887e8883b610be92f0ad98

There's also this:
[https://git.gnome.org/browse/gnome-shell/commit/?id=0e1221561427b84152887e8883b610be92f0ad98](https://git.gnome.org/browse/gnome-shell/commit/?id=0e1221561427b84152887e8883b610be92f0ad98)

Having a friend see what he can do to help restore that functionality, will come back if there's any updates. :)

---

