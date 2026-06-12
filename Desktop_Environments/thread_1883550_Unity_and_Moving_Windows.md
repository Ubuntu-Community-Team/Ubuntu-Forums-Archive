---
title: "Unity and Moving Windows"
date: 2011-11-19
forum: Desktop Environments
---

### Post by schworak on 2011-11-19
I really HATE the UNITY desktop. But it looks like we are being forced down this road so I am trying to get use to it. (I really like a menu driven system because I have lots of stuff to quickly access)


ANYWAY...

I don't know what it is I am touching, but every so often I will be typing and the window that has focus gets these circles on it with arrows. And this lets me move and resize the window. The problem is, some times when it happens the window just jumps off the screen and really makes me mad.

What the heck is it that I am pressing to cause this and how the heck can I disable that "feature"?

I suspect it is some combination of keys and the fact my thumbs drift over my touchpad on the laptop. I have "tapping" turned off and disable "touchpad while typing" turned on.

This is super frustrating so any help would be greatly appreciated.

---

### Post by stinkeye on 2011-11-19
Does it look as in pic.
If so it's the unity Grab Handles plugin.
Use compizconfig-settings-manager to disable it.

---

### Post by schworak on 2011-11-19
That's it.

Only problem now is I can't get  compizconfig-settings-manager to run.

I just installed it from the software center, it says it is installed but no icon and using F2 brings it up but clicking on it does nothing. (looks like gears)

Any suggestions?

---

### Post by stinkeye on 2011-11-19
Enter ccsm in the dash.
If compiz crashes when using ccsm use ctrl+alt+t to open a terminal and run
```
compiz --replace & disown
```

---

### Post by schworak on 2011-11-19
Turns out I just needed to REBOOT after installing compiz before it would work right.

But I disabled that grabber plug in. Thanks so much!

---

### Post by stinkeye on 2011-11-19
No problem.

---

