---
title: "are there other ctrl alt hotkeys that I don't know about"
date: 2009-05-01
forum: General Help
---

### Post by josephellengar on 2009-05-01
So, I've been doing some research about how to reenable ctrl alt backspace, which doesn't work even though I installed and ran the dontzap package, and came across the ctrl alt f2 key combination.  It seems to just restart X, if I figured it out correctly.  Are there any other useful key combos like this?

---

### Post by Peasantoid on 2009-05-01
The ctrl-alt-F* keytrokes don't restart X. They switch you to a virtual terminal, which is sort of like a separate monitor. Press ctrl-alt-F7 to switch back to X (that's *usually* the terminal on which it's running).

To enable ctrl-alt-backspace, just add the following to /etc/X11/xorg.conf:
```
Section "ServerFlags"
    Option "DontZap" "false"
EndSection
```

---

### Post by josephellengar on 2009-05-01
> **Peasantoid said:**
> The ctrl-alt-F* keytrokes don't restart X. They switch you to a virtual terminal, which is sort of like a separate monitor. Press ctrl-alt-F7 to switch back to X (that's *usually* the terminal on which it's running).

To enable ctrl-alt-backspace, just add the following to /etc/X11/xorg.conf:
```
Section "ServerFlags"
    Option "DontZap" "false"
EndSection
```

Thank you.  Can I delete the dontzap package now?  (I didn't know about that whole f* think.  That's kind of neat.)

---

### Post by Peasantoid on 2009-05-01
Yes, go ahead and uninstall dontzap.

---

