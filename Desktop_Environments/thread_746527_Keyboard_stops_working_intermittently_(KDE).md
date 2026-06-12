---
title: "Keyboard stops working intermittently (KDE)"
date: 2008-04-05
forum: Desktop Environments
---

### Post by crouchingturbo on 2008-04-05
[Searched and found some similar problems, but nothing quite like this, and no solutions.]

I'm using my Kubuntu system remotely over FreeNX (Windows nxclient -> Kubuntu nxserver).  It worked perfectly (for months) until just recently.

In the past week, the keyboard has randomly started becoming unresponsive.  I'll log in, actively use the session for 20 or 30 minutes, and then the keyboard will just cut out.  The mouse works fine and the session seems to be completely normal, except for the lack of a functional keyboard.  Starting xev (copying and pasting commands into a terminal with the mouse), there are ZERO keyboard events reported, no matter what key / key combo I press.

Some of the other threads I found relate to xscreensaver, but I'm not running any screensaver.  It is not the accessibility features "slow keys", etc, I made sure to disable all those.

I am unable to determine if it's nxclient, KDE, or X.org that I should blame.  The reason I suspect it's not the client is because I can disconnect the client, reconnect from a Linux nxclient, and the keyboard is still unresponsive.  So it seems like an X server issue.  Also, after screwing around with the machine for 20 minutes or so, the keyboard will come back to life, and start working without issue again.

One thing I *think* I've noticed, is that it seems to stop working when I'm switching desktops in KDE, using CTRL+F1, CTRL+F2, etc.  It seems like a couple quick desktop switches might cause this, but I have only encountered it a few times, so it's not necessarily a good sample set...

ANY ideas would be appreciated, this issue is a killer to productivity.

---

### Post by twist2b on 2008-04-05
I had a similiar problem, my keyboard would work but i would get errors when pressing things like the windows key

go into recovery mode and type this
apt-get update (I always do this just because it helps sometimes)
dpkg-reconfigure xserver-xorg (this is to edit stuff)
leave EVERYTHING alone just keep pressing enter, BUT when on keyboard choose pc150 I think, there is a list of the main ones, I dont know what computer you have, please post your specs! you would be suprised how much this helps.

but the list will tell you which to choose, unless your like british or something....

if the change in keyboard settings does not help, try re-installing KDE.

---

### Post by crouchingturbo on 2008-04-10
[http://bugs.kde.org/show_bug.cgi?id=155951](http://bugs.kde.org/show_bug.cgi?id=155951)

That appears to be my bug..

---

