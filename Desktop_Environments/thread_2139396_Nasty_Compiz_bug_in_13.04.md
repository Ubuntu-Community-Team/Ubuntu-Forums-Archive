---
title: "Nasty Compiz bug in 13.04?"
date: 2013-04-26
forum: Desktop Environments
---

### Post by durrell on 2013-04-26
I've been running 13.04 for weeks without a single issue. I did an update, upgrade, and dist-upgrade last night and finally got around to rebooting this morning. Now I can't run for longer than 3 minutes or so without Compiz crashing.

At boot, I get an error saying the desktop config file can't be loaded and then it reverts to mirror mode. I go to reset my screen layout (dual monitors) and then..

Syslog says:

```

WARNING: Application 'compiz.desktop' killed by signal 7
WARNING: App 'compiz.desktop' respawning too quickly
CRITICAL: We failed, but the failwhale is dead. Sorry...

```

Not running any proprietary drivers. Running an AMD Trinity GPU/CPU combo. No problems before this.

Any ideas? Really frustrated that I had a perfectly functional system, updated, and now it's unusable. :(

---

### Post by durrell on 2013-04-29
I've messed around with this a bit more and found that it's not the dual screens that cause an issue. It's dual screens with different resolutions. It will run fine in extended mode as long as the resolutions match, but when using the "Displays" tool in System Settings to change the secondary screen's resolution, Unity crashes and won't recover.

Anyone?

---

### Post by durrell on 2013-04-29
For what it's worth, this is very similar to what I'm experiencing.

[http://askubuntu.com/questions/288034/i-need-help-resolving-dual-display-issues-with-13-04-running-the-ati-radeon-open](http://askubuntu.com/questions/288034/i-need-help-resolving-dual-display-issues-with-13-04-running-the-ati-radeon-open)

Although, Unity is running perfectly fine as long as the displays have matching resolutions.

---

