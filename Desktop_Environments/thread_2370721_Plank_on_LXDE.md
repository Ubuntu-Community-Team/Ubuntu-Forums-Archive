---
title: "Plank on LXDE"
date: 2017-09-06
forum: Desktop Environments
---

### Post by The Frenchman on 2017-09-06
I'm running Lubuntu 14.04 netbook version I loaded plank,but it won't appear when I log on.If I launch it in terminal it will only work if I don't close the terminal.This is what the terminal reads.
simon@simon-AOA150:~$ plank
[WARN 17:03:02.806953] Couldn't connect to accessibility bus: Failed to connect to socket /tmp/dbus-sBGehg2D3G: Connection refused
[WARN 17:03:02.829324] [Environment:161] XDG_SESSION_CLASS not set in this environment!
[WARN 17:03:02.829750] [Environment:192] XDG_SESSION_TYPE not set in this environment!
[WARN 17:03:02.905064] [Wnck] Unhandled action type _OB_WM_ACTION_UNDECORATE
[WARN 17:03:02.936248] [Wnck] Unhandled action type _OB_WM_ACTION_UNDECORATE
[WARN 17:03:03.265031] [Preferences:192] '/usr/share/plank/themes/Default/dock.theme' is read-only!
[WARN 17:03:06.452947] Creating surface took WAY TOO LONG (139ms), enabled downscaling for this cache!
[WARN 17:03:06.556577] Creating surface took WAY TOO LONG (83ms), enabled downscaling for this cache!
[WARN 17:03:06.617558] Creating surface took WAY TOO LONG (55ms), enabled downscaling for this cache!
[WARN 17:03:06.731048] Creating surface took WAY TOO LONG (98ms), enabled downscaling for this cache!
[WARN 17:03:06.816767] Creating surface took WAY TOO LONG (80ms), enabled downscaling for this cache!
[WARN 17:03:06.910791] Creating surface took WAY TOO LONG (88ms), enabled downscaling for this cache!
[WARN 17:03:07.009085] Creating surface took WAY TOO LONG (83ms), enabled downscaling for this cache!
[WARN 17:03:07.051289] Creating surface took WAY TOO LONG (36ms), enabled downscaling for this cache!
Any clues on how I can get it to launch normally?

---

### Post by vasa1 on 2017-09-06
Lubuntu 14.04 has reached "End of Life" and is no longer supported: [https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29)

---

### Post by Dennis N on 2017-09-06
> I'm running Lubuntu 14.04 netbook version I loaded plank,but it won't appear when I log on.

You need to add it to startup applications. Then it will appear after log in.

---

### Post by The Frenchman on 2017-09-06
> **vasa1 said:**
> Lubuntu 14.04 has reached "End of Life" and is no longer supported: [https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29](https://wiki.ubuntu.com/Releases#End_of_Life_.28EOL.29) Sorry should have said it's LTS version

---

### Post by The Frenchman on 2017-09-06
> **Dennis N said:**
> You need to add it to startup applications. Then it will appear after log in.
Can i do that in terminal? If so what would I enter?

---

### Post by ajgreeny on 2017-09-06
> **The Frenchman said:**
> Sorry should have said it's LTS version
But the LTS versions of Lubuntu are supported for 3 years only, not 5 years like Ubuntu, so, I'm afraid Lubuntu 14.04 is EOL even though it is an LTS version.

---

### Post by Dennis N on 2017-09-06
Menu > Preferences > Default Applications for LX Session > (Press) 'Autostart' on left
On right, next to Add button, enter **plank**. Press 'Add'.
On reboot, it will show up.

I have it installed here and it works.

Note on support for Lubuntu 14.04: you probably notice that the updates are still working, and repositories are open, so it seems like you are still fully supported. But, after 3 years time (now expired), you get no updates to any LXDE or Lubuntu specific packages (like lxsession, lxpanel, lxappearance, and so on). You are still getting security and other updates for packages that are in common with Ubuntu. 

The recommendation is to update to 16.04 or 17.04 (which is the best so far).

---

### Post by The Frenchman on 2017-09-07
> **Dennis N said:**
> Menu > Preferences > Customized Look and Feel > (Press) 'Autostart' on left
On right, next to Add button, enter **plank**. Press 'Add'.
On reboot, it will show up.

I have it installed here and it works.

Note on support for Lubuntu 14.04: you probably notice that the updates are still working, and repositories are open, so it seems like you are still fully supported. But, after 3 years time (now expired), you get no updates to any LXDE or Lubuntu specific packages (like lxsession, lxpanel, lxappearance, and so on). You are still getting security and other updates for packages that are in common with Ubuntu. 

The recommendation is to update to 16.04 or 17.04 (which is the best so far).
Thank you Gents (assumption) for all of you help.I thought because I was still getting updates it was still supported.Given the security updates are common to Ubuntu is it still secure to use.It's a very old netbook with little space left on the hard disc, will updating to 17.04 use much space?

---

### Post by kc1di on 2017-09-07
Lubuntu 17.04 needs about 20 GB of disk space. 
of course that's the min. space needed in reality in order to add programs etc you need much more.

---

### Post by vasa1 on 2017-09-07
> **The Frenchman said:**
> Thank you Gents (assumption) for all of you help.I thought because I was still getting updates it was still supported.Given the security updates are common to Ubuntu is it still secure to use.It's a very old netbook with little space left on the hard disc, will updating to 17.04 use much space?
Well, everything seems to be getting bigger :) So 17.04 probably will take more space than 14.04 currently does. And, if you don't plan to walk on the wild side you maybe okay :) Problems *can* arise when you use an unsupported web browser.

If Dennis N's instructions work for you please mark this thread [SOLVED]: [How to mark threads [SOLVED] or [UNSOLVED]](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads). Thanks!

---

### Post by The Frenchman on 2017-09-08
I did an upgrade to 16.04 with fairly disastrous results.Should I look for assistance on this thread or mark it as solved and start a new one?

---

### Post by vasa1 on 2017-09-08
> **The Frenchman said:**
> I did an upgrade to 16.04 with fairly disastrous results.Should I look for assistance on this thread or mark it as solved and start a new one?

It's better to start a new thread with a nice explanatory title. And you link to this thread if you feel it would help.

---

