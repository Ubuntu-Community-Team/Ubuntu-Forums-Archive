---
title: "Lost graphical login/desktop"
date: 2021-02-23
forum: Desktop Environments
---

### Post by dwilliams2 on 2021-02-23
I recently upgraded to 20.4 and somehow, during that process I seem to have lost the graphical login screen and desktop.  All I have are the tty terminal login options.
I've done some googling today but so far no luck at all.  I'm not that well up on Linux and have have the previous version of Ubuntu running for years without issue.

Before the upgrade I had KDE as my desktop and I am lost as to how to get it back.
Here is what I have done so far:

[LIST]
[*]apt-get install kubuntu-desktop (to ensure everything was installed)
[*]dpkg-reconfigure sddm
[*]cat /etc/X11/default-display-manager gives the following result: /usr/bin/sddm
[/LIST]

When I reboot my box it just shows the following:[INDENT]Terminate Plymouth Boot Screen
Set console scheme
[/INDENT]

I'd appreciate any help/guidance to get this working again.  I know my way around the console but not familiar with too many commands.

---

### Post by dino99 on 2021-02-25
Be sure to use a cleaned system: run autoclean/autoremove to get rid of old packages/settings left behind.
Reboot and look at "journalctl -b" output to know about possible errors (red lines) and harmless warnings (yellow lines).

---

### Post by ActionParsnip on 2021-02-25
If you boot an older kernel does it boot OK?

---

