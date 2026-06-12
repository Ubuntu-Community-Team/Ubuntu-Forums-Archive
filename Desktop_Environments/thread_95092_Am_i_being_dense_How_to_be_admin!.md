---
title: "Am i being dense? How to be admin!?"
date: 2005-11-25
forum: Desktop Environments
---

### Post by sugarat on 2005-11-25
Hi All, 

 Just installed my first Kubuntu system. 

 From the K menu I go into the system settings screen and then try to configure my wireless network by clicking on connections -> wireless networks. I see that as per usual for KDE, I need to click the adminstrator button to make any changes. 

 The problem is, that after I enter the root password for the system all the boxes are still greyed out. This is the same for every control panel, - how on earth am I meant to configure Kubuntu?

 many thanks!

---

### Post by GeneralZod on 2005-11-25
This has been a long-standing bug with Kubuntu, unfortunately, and to fix it you have to download one of the recent updates.

You can get admin mode by doing:

```

sudo kcontrol

```

from a konsole.  It's a nasty hack, but hopefully won't be required once you've downloaded and installed all available updates :)

---

### Post by teaker1s on 2005-11-25
its a bug please add to the bug report the more problems the quicker it will be looked at [here]("https://launchpad.net/distros/ubuntu/+bug/4738")

[here]("http://ubuntuforums.org/showthread.php?t=94944") I suggested a method to resolve it if you haven't created a spare account note it's for gnome but kde should be same or similar

---

### Post by sugarat on 2005-11-25
Oh well, - thanks for clearing that up. Makes sense now, though it is surprising that a bug as big as that made it's way into a general release version!

 Cheers

---

