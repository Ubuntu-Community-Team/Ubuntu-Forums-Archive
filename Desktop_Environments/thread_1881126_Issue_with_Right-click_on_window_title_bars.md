---
title: "Issue with Right-click on window title bars"
date: 2011-11-15
forum: Desktop Environments
---

### Post by ShinIori319 on 2011-11-15
Hello.
I am having a kind of an issue with my desktop's system's windows. When you click on a title bar, a menu should show with options to minimize, maximize, close... But it only appears when holding the Alt key. (There was a time that even this would not respond). I managed to find an option in GNOME Tweak tool that seems to fix this, but this change does not save, since upon restarting the title bars do not respond again to the right clicks. This happens in Unity, GNOME Shell and GNOME Classic.
Recently I installed Ubuntu in a netbook as well, and the title bar's menus work as they should.

---

### Post by stinkeye on 2011-11-15
This setting seems to control that setting even when using compiz.
```
gconf-editor /apps/metacity/general/action_right_click_titlebar
```

---

### Post by ShinIori319 on 2011-11-15
> **stinkeye said:**
> This setting seems to control that setting even when using compiz.
```
gconf-editor /apps/metacity/general/action_right_click_titlebar
```
Awesome! It worked, thanks man. Its strange though that GNOME Tweak tool did not seem to save those settings upon logging off.

---

