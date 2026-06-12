---
title: "Steam boots in Unity, but not Xubuntu or Lubuntu"
date: 2015-01-02
forum: Gaming &amp; Leisure
---

### Post by Cleaver on 2015-01-02
Hi,

I have Steam installed in Ubuntu 14.10. It loads fine while in Unity, but if I logout and boot into Xubuntu/Lubuntu(using the installable ones that are found in the Software Center by the names xubuntu-desktop and lubuntu-desktop,) Steam won't run within those. It *does* show up in the menu as it should in both, though. Any idea why this would be the case?

The reason I have those installed is because some things(especially games!) can get a good boost in speed from using xfce or especially lxde.

Thanks in advance.

---

### Post by efflandt on 2015-01-02
Steam used to have a problem if you ran Steam as one Linux user, exited Steam, then logged in as a different user and ran Steam, because it left something lingering in /tmp with only permissions for the first user (the 1st user could run Steam again no problems). That did not really stop Steam from running, it just made it extremely sluggish because it buried one CPU core at 100%. But they may have fixed that because I just ran Steam and did not see that directory in /tmp anymore.

How did you install Xubuntu/Lubuntu as alternates. I added Lubuntu to Ubuntu per [http://askubuntu.com/questions/228503/is-it-possible-to-use-multiple-desktop-environments-on-same-system](http://askubuntu.com/questions/228503/is-it-possible-to-use-multiple-desktop-environments-on-same-system) (using --no-install-recommends) to see what difference there was in graphic benchmarks without compiz, but it was insignificant (1-2 fps gain) for my GTX 750 Ti. The desktop fonts in Lubuntu are extremely tiny at 1080p. I just launched Steam from Lubuntu desktop and played a training map in Team Fortress 2, and everything worked fine.

Try launching steam from a terminal in X and see what error(s) you get.

Fresh 64-bit 14.04.1 about 2 days ago using nvidia 346.22 drivers from xorg-edgers ppa (nvidia-current 304 driver was years too old and did not support Maxwell chips). Before that I had been running 64-bit 12.04 w/nvidia 331 driver (which worked fine). Linux Steam user since Jan 2013.

PS: Just noticed you have 14.10 which I have not tired yet.

---

### Post by Drowz0r on 2015-01-07
I have a similar problem ever since the .1 update in Lubuntu. A bunch of little problems like the Lubuntu splash screen not being 100% were fixed but now Lubuntu boots without the desktop on my laptop and Steam won't boot in Lubuntu on my PC. Steam does boot absolutely fine on my desktop in Ubuntu however.

In Lubuntu Steam will open, seemingly update, then prompt for username and password, upon entering it seemingly tries to connect, then loops back to username and password. It continues to to this either endlessly or just crashes after a few attempts, closing steam down completely.

During this looping, the steam icon will appear on the status bar for a moment too.

14.04 LTS versions on all desktops.

---

