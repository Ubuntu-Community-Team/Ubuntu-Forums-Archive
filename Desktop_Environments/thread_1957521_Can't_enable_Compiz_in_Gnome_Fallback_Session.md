---
title: "Can't enable Compiz in Gnome Fallback Session"
date: 2012-04-12
forum: Desktop Environments
---

### Post by N00b-un-2 on 2012-04-12
I just did a fresh install of 11.10 on my HTPC and I'm using Gnome classic.  I have an nVidia graphics card (GeForce GT 430), which I know to work just fine on several versions of Ubuntu.  I've tried installing both of the drivers available in Jockey as well as the Nouveau driver.  Can't enable compiz no matter what I do, and there are no error indications when I type compiz --replace ccp in the terminal.  Metacity compositing works fine though.

---

### Post by roelforg on 2012-04-12
It's called "gnome **fallback**" for a reason...

Spoiler:
Because it's used when compiz has troubles.
Check the logs, should be somewhere in /var/log

---

### Post by N00b-un-2 on 2012-04-12
nevermind.  I fixed it.  setting the window decorator plugin back to default was the trick.
And quite frankly, in my experience using gnome fallback, its a far less irritating and user unfriendly than gnome-shell or unity.  Fallback session absolutely should be the default.  Unity is terrible, Shell is just as bad, but at least shell is not a massive deviation from the rest of the Linux world.  I seriously can't figure out what these developers are thinking.

---

