---
title: "Cannot enable/disable plugins via main CompizConfig Settings Manager"
date: 2007-10-24
forum: Desktop Effects &amp; Customization
---

### Post by riverfr0zen on 2007-10-24
In the main screen of the CompizConfig Settings Manager, all the checkboxes next to the plugins  are grayed out, and I cannot enable or disable plugins from that screen. I can, however, click on the plugins and configure their settings.

Also, if I go into Preferences and click on the Plugin List tab, I am able to enable/disable plugins from there.

Any idea why the main screen checkboxes may be grayed out for me? Thanks.

---

### Post by DariusS on 2007-10-24
Just taking a shot out in the dark here - also assuming use of 7.10 - but have you tried going to settings> Appearance Preferences then visual effects tab and enabling the desktop effects first?

---

### Post by riverfr0zen on 2007-10-24
Yeah, 7.10 - sorry for not specifying - been reading a lot of Gutsy threads here, and just sort of assumed it was assumed :) 

Yes, I have Visual Effects set to Custom. I had messed around with the Emerald themer a little, then uninstalled it - I wonder if that somehow blocked these settings ... though not sure how that would be.

---

### Post by DariusS on 2007-10-24
well, the way I understand it, Emerald is mainly a GUI like the Compiz util that Gutsy comes with, so if there are still some residual packages/files from an emerald install, I'd think its possible to cause interference....

---

### Post by arvinoids on 2007-12-09
I also have the same problem. I have browsed some threads in the forum and I may have to try one trick, maybe it can work. That is, switching to flat-file backend. I believe the problem started when I tried to load a configuration file with a gconf backend. Please do post updates.

---

### Post by SanskritFritz on 2007-12-10
Switch on the Automatic Plugin Sorting option in Preferences / Plugin List
HTH

---

### Post by arvinoids on 2007-12-11
> **SanskritFritz said:**
> Switch on the Automatic Plugin Sorting option in Preferences / Plugin List
HTH

Yep, I kinda figured that out too before I saw your post. lol. Thanks anyway! :)

---

