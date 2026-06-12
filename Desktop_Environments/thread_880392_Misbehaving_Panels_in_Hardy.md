---
title: "Misbehaving Panels in Hardy"
date: 2008-08-04
forum: Desktop Environments
---

### Post by raywood on 2008-08-04
I'm working along.  I click on a box on the bottom panel and, boom, my desktop vanishes.  I am staring at a black-and-white screen with commands I don't understand.  After a minute or so, without doing anything further, I'm back at the login prompt.

Upon logging in, I see that my panels have moved.  The top panel, which I had put at the right side of the screen, is now on the left side.  The bottom panel is now at the top.  When I right-click on either of these and designate a different location, they ignore me and, right there in the Panel Properties dialog box, they immediately switch back to where they were.  So, for example, the one says "Top."  I change it to "Right."  It switches right back to saying "Top."

In Terminal, I type killall gnome-panel.  The panels vanish for a moment and then return to where they were a moment earlier.  Same thing if I type sudo killall gnome-panel.  It seems I can't move them and I can't kill them.  I rebooted and still got the same thing.

Any clues to this mystery?

---

### Post by K2712 on 2008-08-05
Do the following to reset your panels to default settings:


Back up panel settings first(just in case):
```
cp -R ~/.gconf/apps/panel ~/panel_bak
```

Delete current panel profiles:
```
rm -r ~/.gconf/apps/panel
```

Now log out and back in and your panels should be at their default settings and you can change them however you want.

---

