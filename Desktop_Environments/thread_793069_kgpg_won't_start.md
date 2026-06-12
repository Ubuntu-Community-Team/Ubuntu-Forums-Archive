---
title: "kgpg won't start"
date: 2008-05-13
forum: Desktop Environments
---

### Post by mvaniersel on 2008-05-13
Kgpg is the GUI key manager for gpg keys, without a gnome equivalent. Since I installed hardy, I can't start the program kgpg anymore. When I try from the command line I get these error messages:

```
~$ kgpg
DCOPClient::attachInternal. Attach failed Could not open network socket
DCOPClient::attachInternal. Attach failed Could not open network socket
kbuildsycoca running...
DCOP Cleaning up dead connections.
```

Then I get a new prompt and that's it.
Anybody seeing the same? Any ideas where to begin trouble shooting?

---

### Post by r_avital on 2011-11-18
I know this is old...

Install kgpg from synaptic, and run it as root from a terminal:

sudo kgpg

After you enter your password you'll see messages in the terminal, then you'll get your prompt back, and there should be an icon in your gnome notification area.

Problem is, even if you configure kgpg to start automatically when you log in, if you're in gnome, it won't start.  I'm still looking for an answer to that.

And by the way, gnome-gpg is not an equivalent, it's a command line utility.  Nothing wrong with that, but it's not a GUI gpg key manager like kgpg.

---

### Post by oldos2er on 2011-11-18
> **r_avital said:**
> I know this is old...

Indeed it is. Please don't bump old threads.

---

