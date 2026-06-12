---
title: "Xubuntu 11.04: Shutdown doesnt work properly"
date: 2011-05-10
forum: Desktop Environments
---

### Post by silentcreek on 2011-05-10
Hi,

with the new Xubuntu 11.04 I encounter an issue when shutting down the system. Often, when I click on shutdown, the computer doesnt shut down but just logs off and shows me the login screen where I have to select shut down again. It's somewhat annoying. However, sometimes (rarely) it works properly.

Does anybody have the same issue and know a solution?

Thanks,

Timo

---

### Post by peabrane on 2011-05-10
I have a similar problem on an ancient beaten-up old HP OmniBook 6000 laptop. As far as I can tell, it always shuts down OK when on power but 75% of the time does not shut down when on battery. I guess that this is some sort of issue with the power settings. I have no idea what though. I did fiddle with some power settings via the settings manager but to no avail.

As with Timo, I then have to shut down from the log-in screen. Didn't have this prob with earlier versions of xubuntu, only 11.04.

I also would be interested in any advice in solving this.

---

### Post by ManualSparrow on 2011-05-10
Try adding the 'action buttons' button to the panel instead of the 'session manager' one. Does the rightclick menu logout menu work?

---

### Post by Qazer on 2011-05-10
This is likely [https://bugzilla.xfce.org/show_bug.cgi?id=7442](https://bugzilla.xfce.org/show_bug.cgi?id=7442)

---

### Post by silentcreek on 2011-05-11
> **peabrane said:**
> As far as I can tell, it always shuts down OK when on power but 75% of the time does not shut down when on battery.
I'm not running Xubuntu on a laptop, so for me I can rule that out.

Thanks,

Timo

---

### Post by silentcreek on 2011-05-11
> **ManualSparrow said:**
> Try adding the 'action buttons' button to the panel instead of the 'session manager' one. Does the rightclick menu logout menu work?
I just tried that, but it doesnt help. The logout works fine, but the shutdown shows the same behaviour - leading me to the login screen.

Thanks,

Timo

---

### Post by ManualSparrow on 2011-05-11
After uninstalling some things from Gnome, I now have the same problem and the login screen (gdm) is now blockier than it used to be and has only a black background.

EDIT: Reinstalled StartupManager, which installs some Gnome utilities but reenables the splash screen (which is disabled with Nvidia drivers for some reason) and, apparently, makes shutdown work properly.

---

### Post by peabrane on 2011-05-11
Thanks for the suggestions......

Tried installing StartupManager. Still the same problem.

Am already using the 'action buttons' to shut-down (or attempt to).

---

### Post by ManualSparrow on 2011-05-11
I simultaneously reinstalled GDM and the associated Xubuntu GDM themes, so that may have helped although it isn't a fix on its own (confirmed this). Your problem may have a different origin.

---

