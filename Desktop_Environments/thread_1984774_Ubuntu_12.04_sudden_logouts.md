---
title: "Ubuntu 12.04 sudden logouts"
date: 2012-05-22
forum: Desktop Environments
---

### Post by vanjalee on 2012-05-22
I just recently updated to 12.04 and my computer started loging me out automatically.
It is not the screensaver or screen lock issue. Computer is not idle when it happens, it even happens when I work in eclipse.
The screen just goes black for a couple of seconds, and after that I am sent back to login screen.
Apart from that, it happens in a pretty weird way: it first happens after 30 minutes. Next time I log in it happens after like 20, than after 15...

My computer is pretty strong (2.75GHz x 4, 4Gb, G-force 1500Mb) so I don't think the overheating should be an Issue. I didn't have this problem with previous version, and I never had this problem in Win 7, which is the second OS on my computer.

Any suggestions will be appreciated!

Vanja

---

### Post by redsparrow on 2012-05-22
I'm still on 11.10 and I'm having a similar problem.

I'm back at work after a long weekend (Monday was a holiday here) and did a system update.  Off the top of my head I remember there being a ubuntu-minimum (or something similar) and a bunch of vim updates.

I haven't been paying attention to the timing, but twice so far this morning my machine has quite suddenly dumped me to the lightdm login screen.  I use Gnome Shell (rather than Unity.)  Both times it's happened I've been actively using my computer.

Once I'm back at the login screen I'm unable to get to a tty login using ctrl-alt-f1.  My monitor says "no signal."  Going back to X (ctrl-alt-f7) works.  I've rebooted after each incident this morning.

This is going to make it hard to get much work done today.  :(

Here is a list of updates I applied this morning:
```

Setting up vim-common (2:7.3.154+hg~74503f6ee649-2ubuntu3.1) ...
Setting up vim-runtime (2:7.3.154+hg~74503f6ee649-2ubuntu3.1) ...
Setting up vim (2:7.3.154+hg~74503f6ee649-2ubuntu3.1) ...
Setting up vim-gui-common (2:7.3.154+hg~74503f6ee649-2ubuntu3.1) ...
Setting up vim-gnome (2:7.3.154+hg~74503f6ee649-2ubuntu3.1) ...
Setting up vim-tiny (2:7.3.154+hg~74503f6ee649-2ubuntu3.1) ...
Setting up ubuntu-minimal (1.245.1) ...
Setting up ubuntu-standard (1.245.1) ...
Setting up python-desktopcouch-records (1.0.8-0ubuntu1.1) ...
Setting up python-desktopcouch-application (1.0.8-0ubuntu1.1) ...
Setting up desktopcouch (1.0.8-0ubuntu1.1) ...
Setting up libmission-control-plugins0 (1:5.9.1-0ubuntu2.1) ...
Setting up telepathy-mission-control-5 (1:5.9.1-0ubuntu2.1) ...
Setting up ubuntu-desktop (1.245.1) ...
Setting up libxml2 (2.7.8.dfsg-4ubuntu0.3) ...
Setting up libxml2-dev (2.7.8.dfsg-4ubuntu0.3) ...
Setting up libxml2-utils (2.7.8.dfsg-4ubuntu0.3) ...
Setting up python-libxml2 (2.7.8.dfsg-4ubuntu0.3) ...

```

...

10:30.  Had another crash.  This time after about 15 minutes.  Instead of dumping me to lightdm the screen froze.  I could move the cursor but the computer was unresponsive to clicks and keyboard.  I was able to ssh from another machine to issue reboot.

---

### Post by redsparrow on 2012-05-22
I haven't had any problems for over an hour.

I rolled-back the desktopcouch packages at about 10:45, had another dump to lightdm at about 10:55 which I followed with a reboot.  I haven't had any problems since.  If it's still working in another hour or so I'll raise a ticket with the couch folks.

To anyone else having this problem, let me know if this downgrade helps you.

```

sudo apt-get install desktopcouch=1.0.8-0ubuntu1 python-desktopcouch-records=1.0.8-0ubuntu1 python-desktopcouch-application=1.0.8-0ubuntu1

```

Edit...

After two hours of uptime I tried re-updating the three packages listed above to see if the problem would come back and it did.  About 10 minutes after updating I was dumped into lightdm.  I've once again downgraded the packages.

Edit...

I've created a ticket:

[https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/1003028](https://bugs.launchpad.net/ubuntu/+source/desktopcouch/+bug/1003028)

---

### Post by redsparrow on 2012-05-22
Maybe I spoke too soon.  I just had some gnome shell crashes while running the non-updated version (1.0.8-0ubuntu1) of desktopcouch, et al.

Opening the gnome shell application list (by pushing the super/windows key) and then searching for an app by typing its name caused gnome shell to crash and restart.  Doing it a second time causes it to crash without restarting.

I missed it earlier but it looks like I'm having GPU errors.
Seeing some messages in kern.log around the time of various crashes:

"NVRM: GPU at 0000:02:00.0 has fallen off the bus."
and
"gnome-shell[3625]: segfault at 10 ip 00007fd8ea8ebc0f sp 00007fd8dbdfe638 error 6 in libnvidia-tls.so.295.20[7fd8ea8eb000+3000]"

Saw the first message on a couple (but not all) of the crashes to lightdm this morning and the segfaults are happening each time I do a search in the gnome shell applications menu.

Plus I'm currently running *with* the new desktopcouch updates and have an uptime of 41 minutes.

Need to keep digging...

Edit...

I found that my NVIDIA drivers were using the "current-updates" branch rather than "current".  Switching back to "current" changed my driver version from 295.20 to 280.13.  That seems to have fixed at least the segfaults.  Now just need to wait-and-see on the logouts...

Edit...

43.5 hours after changing my NVIDIA drivers and I haven't had any unexpected logouts or segfaults.  Looks solved for me.

---

### Post by simontornros on 2012-08-23
Changing drivers to "NVIDIA acceleraded graphics driver (post-release updates)(version 173-updates)" seems to have solved this problem for me. Ive got a NVIDIA G84 and was randomly logged out about 5 times a day before I changed drivers. So far no log outs the last two days.. :popcorn:

---

