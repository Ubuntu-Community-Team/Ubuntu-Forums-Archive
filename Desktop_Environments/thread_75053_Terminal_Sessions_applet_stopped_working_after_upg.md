---
title: "Terminal Sessions applet stopped working after upgrade"
date: 2005-10-13
forum: Desktop Environments
---

### Post by thumper on 2005-10-13
The terminal sessions applet (button on the kicker) used to show a menu like:
[LIST]
[*]Shell
[*] Linux console - which was very much like shell
[*] Python interpreter
[*] Root shell
[/LIST]
But now nothing.  Just no response to a click at all.

Any ideas?

---

### Post by mlomker on 2005-10-13
No, but I see what you're talking about and it works on mine.  You have tried removing and adding it back?  It looks like that's basically the Session menu from Konsole.  Maybe try reinstalling it?

```

sudo apt-get install --reinstall konsole

```

---

