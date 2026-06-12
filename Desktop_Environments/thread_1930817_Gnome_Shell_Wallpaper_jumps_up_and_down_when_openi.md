---
title: "Gnome Shell: Wallpaper jumps up and down when opening Activities"
date: 2012-02-24
forum: Desktop Environments
---

### Post by The Bright Side on 2012-02-24
Hello Ubuntu lovers! Has anybody experienced this: when opening the "Activities" overview in Gnome Shell, the wallpaper jumps up. It seems like it's anchored to the panel by the top edge, rather than anchored to the bottom of the screen by the bottom edge.

Any way to change that behaviour? I'm sure a simple CSS edit somewhere will do it... But I don't know where to look.

---

### Post by oldos2er on 2012-02-24
Moved to Desktop Environments.

---

### Post by The Bright Side on 2012-02-24
Thanks oldos2er, I noticed after posting that it belongs there, but could not find out how to move it myself.

---

### Post by Copper Bezel on 2012-02-24
I think you're experiencing a problem where the Nautilus backdrop renders a menubar. You can't see it, because it's under your opaque panel, but it pushes the wallpaper down. When you switch to the Overview, the Nautilus backdrop disappears (which would normally just mean that any desktop icons disappeared, but due to the menubar, the Nautilus wallpaper and that of the root window don't line up.)

Try this fix, from a user named Krytarik, to disable the menu bar:

```
echo '[ "$DESKTOP_SESSION" != "ubuntu" ] || [ "$DESKTOP_SESSION" != "ubuntu-2d" ] && unset UBUNTU_MENUPROXY' | sudo tee /etc/X11/Xsession.d/81ubuntu-menu-proxy
```

Reset the Shell and see what happens.

---

### Post by The Bright Side on 2012-02-25
Hey Copper Bezel, thanks for the tip! Does this code go into the terminal? I executed the commands, reset and the behaviour remains the same.

EDIT: forget the above, it works after restart! Thanks!

---

### Post by Copper Bezel on 2012-02-26
Yeah, I should have mentioned that. Sorry about that! But I'm glad it worked for you.

---

### Post by deciding39 on 2012-03-10
Thanks for this, it's been driving me crazy! I've been searching for a fix for a week or two but I must have been describing the problem incorrecty. Worked perfecly after logging out and back in on 11.10 32-bit.

---

