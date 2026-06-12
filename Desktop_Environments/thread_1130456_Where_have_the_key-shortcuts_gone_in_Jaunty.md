---
title: "Where have the key-shortcuts gone in Jaunty?"
date: 2009-04-19
forum: Desktop Environments
---

### Post by jjalocha on 2009-04-19
Anyone knows what happened to these useful keyboard shortcuts in Xubuntu Jaunty?

[LIST]
[*]Resize Window: ALT+SHIFT+ARROW
[*]Move Window: CTRL+ALT+SHIFT+ARROW
[*]Kill X.org session: CTRL+ALT+BKSP
[/LIST]

Are they gone forever, or is this a bug? Is it possible to "configure them back" anyhow?

---

### Post by PacSci on 2009-04-19
Ctrl+Alt+Backspace should ALWAYS work. If it doesn't, you have a serious problem.

As for resize and move, you might have to check the window manager settings for that.

I'd check Launchpad, though, and see if anyone else has mentioned this.

---

### Post by jjalocha on 2009-04-19
Hmmm.... CTRL+ALT+BAKSP does not work here... maybe it has to do with this @#!*#*! Spanish keyboard? (They don't sell US keyboards here in this country!)

I'll look into Launchpad...

---

### Post by MadCow108 on 2009-04-19
ctrl alt backspace has been disabled in jaunty:
[https://wiki.ubuntu.com/XorgCtrlAltBackspace](https://wiki.ubuntu.com/XorgCtrlAltBackspace)

resizing is alt F8 now and moving alt f7
can be configured in the settings manager udner windows manager->keyboard

---

### Post by jjalocha on 2009-04-19
MadCow, thank you very much for your informative post.

Personally I don't like any of these changes, but both seem to come from "upstream". CTRL+ALT+BKSP can be reset in xorg.conf. And resize is now an intricate multi-step function, probably implemented in the new Xfce 4.6, which can't be mapped to simple key-strokes any longer.

---

