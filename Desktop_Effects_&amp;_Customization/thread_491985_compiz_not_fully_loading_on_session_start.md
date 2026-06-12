---
title: "compiz not fully loading on session start"
date: 2007-07-04
forum: Desktop Effects &amp; Customization
---

### Post by Chriss.Hi on 2007-07-04
Since I installed/uninstalled beryl I've a problem: My compiz doesn't fully start up... It seems that it's loaded, but window-decorations are missing. If I type "compiz --replace" in the terminal it loads correctly! So why doesn't it start with the session? (it's activated in the desktop-effects tool)

---

### Post by Happy_Man on 2007-07-04
Do you have Emerald installed? Try running ```
emerald --replace
```

---

### Post by Chriss.Hi on 2007-07-04
Yes it works.
But my problem is another: The compiz window borders _do work_ with "compiz --replace" manually typed in the terminal but not on the session start! But if I add it to the programs that should be started on session start manually, it doesn't work (it the same command "compiz --replace", but the only result is, that metacity is not loaded...)

---

### Post by Happy_Man on 2007-07-04
That's odd.... I'm afraid I have no idea what may be causing that problem. More than likely it will be resolved with the next update.

---

### Post by Bd0g on 2007-07-04
You're not alone buddy, that error is one of mine too..

---

### Post by WeyOh on 2007-07-05
Same thing here. Is there no way to make it start by adding it in the startup programs in the preferences>sessions? I tried once but messed all up...

---

### Post by Chriss.Hi on 2007-07-06
It's not working for me either.
Looks like it's a known problem:
Look into the script /usr/bin/compiz (yes that's a script)
and you'll find some a line where it says:
# Fix bug loading this script on a gnome session [Fixed? Not for all! :/]
Anyone knows about a launchpad entry?

---

