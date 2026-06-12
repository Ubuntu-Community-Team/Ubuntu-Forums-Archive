---
title: "[SOLVED] Screenlets no longer launch at bootup"
date: 2007-08-14
forum: Desktop Effects &amp; Customization
---

### Post by PaulFXH on 2007-08-14
I've been using screenlets and compiz-fusion together for sometime without any problems.
However, since an automatic update on screenlets yesterday, they no longer launch on booting.
I can still get them to work by going Applications>Accessories>Screenlets and "adding " the ones I want. When I click these they immediately go to the position they were left in before shutdown (as normal).
But why won't they launch at startup?
The command I am using in System>Preferences>Sessions>Start-Up programs is "screenlets-tray". Has this changed?
Paul

---

### Post by FuturePilot on 2007-08-14
Yes. Things changed in the latest version 0.9. I'm still trying to figure out how to get them to autostart when I login too. It seems as though screenlets are no longer controlled by a daemon. Instead it looks as though they run individually. So the screenlets-tray command will no longer work since screenletsd is no longer used. I hope someone can tell us how to get them to start automatically.

And where did all the screenlets go? I want the weather one back.

---

### Post by PaulFXH on 2007-08-14
I posted on the [Screenlets forum]("http://forum.compiz-fusion.org/index.php")  and was advised that each screenlet must now be added individually to System>Preferences>Sessions>Startup Programs.
This is the type of command needed for each screenlet:
```
/usr/local/share/screenlets/Clock/ClockScreenlet.py
```

---

### Post by FuturePilot on 2007-08-14
That's what I was about to try. Thanks :)

---

