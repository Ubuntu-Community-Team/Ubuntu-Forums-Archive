---
title: "Howto - Return Compiz to default settings"
date: 2009-04-18
forum: General Help
---

### Post by zwyber on 2009-04-18
People like me play around with Compiz, but when you mess up you don't have a clue what to do to revert the problem. I had that just today, and finally found a solution.

NOTE:
This only works if you have used the gconf backend for compiz settings (default)

1. Fire up your system in recovery mode.
2. When the blue selection screen shows up, choose "root  Drop to root shell prompt"
3. Type in: (What this does is it removes the list with plugins compiz has to load, and so forces it into default settings.)
```
gconftool-2 -u /apps/compiz/general/allscreens/options/active_plugins
```
4. Type in: (To restart your system)
```
reboot now
```

Now fire up your system like always, and hopefully it worked!

PS: I am sorry, but I don't check this forum very often so replies may not get read.

---

