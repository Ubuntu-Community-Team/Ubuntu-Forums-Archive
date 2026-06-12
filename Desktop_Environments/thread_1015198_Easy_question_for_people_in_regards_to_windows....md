---
title: "Easy question for people in regards to windows..."
date: 2008-12-18
forum: Desktop Environments
---

### Post by d-d-d-d-d-d-card on 2008-12-18
HI, after reinstalling Gnome and NAutilus, i rebooted my pc to find a few changes, such as  larger text, etc.

I've sorted out all the major things so that my ubuntu looked like before, but now when I open windows they ALWAYS maximise, which is annoying, and the.. I don't know what you'd call it... title bar... of each window where before there would usually be an exit, maximise, and minimise symbol is not present.

I also can't drag windows about with having to hold in the 'alt button' arggghh

I've looked everywhere in settings to fix this, but I can't find where to edit these particular settings.. can anyone help?

---

### Post by Achetar on 2008-12-18
Delete the .gnome and .gconf2 and .gtkrc files in your home directory. That should reset everything back to defaults (ie Live CD defaults)

---

### Post by d-d-d-d-d-d-card on 2008-12-18
Those are hidden files, yeah?

HOw do I enable viewing of these? Ive never had to do this before xD

---

### Post by Izek on 2008-12-18
> **d-d-d-d-d-d-card said:**
> Those are hidden files, yeah?

HOw do I enable viewing of these? Ive never had to do this before xD

Right-click a blank space in the file manager and there's an option for it.

---

### Post by Ludachrispeed on 2008-12-18
This problem happens to me with Firefox... I usually use opera so it was never super annoying...

In order to close Firefox, I open up a Terminal and type

```
ps -A | grep firefox
```

which searchas all the active processes for firefox.

It returns something like...

7696 firefox

Then I say

```
kill 7696
```

It's a terrible solution, but it's all I could think of. I'm still pretty noobish.

---

