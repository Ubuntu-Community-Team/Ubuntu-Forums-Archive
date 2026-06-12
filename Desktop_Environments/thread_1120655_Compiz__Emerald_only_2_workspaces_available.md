---
title: "Compiz / Emerald only 2 workspaces available"
date: 2009-04-09
forum: Desktop Environments
---

### Post by pan69 on 2009-04-09
Hi.

I've enabled Compiz with Emerald window decorator (seems the only combo that works). But when enabled I only see 2 workspaces available. When I right click and open the preferences for the workspace switcher it indicates there are 4 workspaces available. Changing this number doesn't change anything. There are always only two workspaces available. How do I set it so that my default four workspaces are available again?

Thanks,
Luke

---

### Post by stefan_g on 2009-04-09
Hi,

I had a different though somehow similar problem with workspaces.
I could set the count to a different number, and they actually appeared, however, I could only configure keyboard shortcuts for the first two of them in "System->Preferences->Keyboard shortcuts". Apparently, this tool read the number of workspaces from a gconf setting of metacity. Weird, right?

If your problem is related to mine, you may try the following:
1) Start gconf (open a terminal and type gconf-editor).
2) In there, go to apps -> metacity -> general
3) Find the num_workspaces setting and change it from 2 to 4.

Good luck.

-- Stefan

---

### Post by pan69 on 2009-04-09
Hi Stefan,

Thanks for your quick response. Unfortunately that variable is set to 4. Changing it doesn't make a difference.

Any other ideas?

---

### Post by lightpriest on 2009-04-09
Have you tried using ccsm for it?
I'm using Compiz Config SettingsManager (ccsm for short).
In it you'll see General options, go to Desktop Size tab and change the value.

---

### Post by pan69 on 2009-04-09
Awesome! That was the setting I was looking for. I believe I've gone through about every single compiz setting except of course the ones on the 'general' tab... :)

Cheers!

Happy holidays!

---

