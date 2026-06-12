---
title: "multimedia key shortcuts dont work on login"
date: 2009-12-24
forum: Desktop Environments
---

### Post by gfxmonk on 2009-12-24
Each time I log in (since a few days ago; before that it was fine), my miltimedia-key gnome keybindings don't register. other keyboard shortcuts seem to work as usual still.

As in, when I press (for example) the volume up button, I can see that according to xev the right key events (XF86AudioRaiseVolume) are being generated, but it doesn't change the volume.

When I go to the keyboard shortcut dialog, I see the shortcut is listed as "XF86AudioRaiseVolume", as it should be.

What's weird though, is that I can click it to set the shortcut, and once I set it to that key (which it already *was*) - it starts working again - until next time I log out.

---

### Post by gfxmonk on 2009-12-26
on further searching, it looks like I have this problem:
[https://lists.ubuntu.com/archives/desktop-bugs/2006-August/047797.html](https://lists.ubuntu.com/archives/desktop-bugs/2006-August/047797.html)

that is, my xmodmaprc is being read after gnome-settings-daemon starts, which evidently causes the remapped keys (the multipmedia keys, in my case) to not be recognised. I've added a startup item to kill and restart gnome-settings-daemon as a workaround for now, but if anyone has further info on the bug or its proper resolution, I'm interested...

---

