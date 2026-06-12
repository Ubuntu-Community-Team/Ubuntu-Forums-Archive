---
title: "No Unity (Ubuntu) option at login splash (11.10)"
date: 2011-10-20
forum: Desktop Environments
---

### Post by zombiezparadize on 2011-10-20
Hi,

I upgraded Ubuntu from 11.04 to 11.10. And after a couple of reboots, the options to login to Unity (Ubuntu and Ubuntu 2D) vanished from the login splash screen. The options that I see now are: 
[LIST]
[*]GNOME Classic [COLOR="Red"]selected by default[/COLOR]
[*]GNOME Classic(No effects)
[*]Recovery Console
[*]User Defined Session
[/LIST]

I do have unity installed and it works on my laptop as I am able to start it by executing: 
```
unity --reset
``` from the command line.
But that also means that I lose my unity configuration every time I logout. Could anybody tell me what I could do to get the options for Unity back or which file has this list?

Thanks a bunch

---

### Post by psylent911 on 2011-10-20
I can't offer help but I have slightly similar problem.  I DO have the unity login selection, BUT BUT Unity is not coming up anymore.  It came up this morning but now nothing.

---

### Post by zombiezparadize on 2011-10-20
For that problem, I can offer something you may try. Do you have ccsm installed? If yes, bring it up and go to the "Desktop" settings and see if Unity is enabled. If it is not, then enable it or if it is already enabled, close ccsm. From the command line, try the command I mentioned in the post above:

```
unity --reset
```

That usually does the trick for me. See if it works for you.

---

### Post by zombiezparadize on 2011-11-02
Finally! Reinstalling the Ubuntu desktop package did the trick for me.

```
sudo apt-get install --reinstall ubuntu-desktop
```

---

