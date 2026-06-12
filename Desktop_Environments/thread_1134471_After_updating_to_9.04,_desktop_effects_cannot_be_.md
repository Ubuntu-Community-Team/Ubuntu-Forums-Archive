---
title: "After updating to 9.04, desktop effects cannot be enabled."
date: 2009-04-23
forum: Desktop Environments
---

### Post by murderslastcrow on 2009-04-23
So, although I didn't need restricted drivers while using 8.10, suddenly in 9.04 I can't use desktop effects. Might be an issue with the new Intel driver package, but I'd like to keep the newest files possible.

"VGA compatible controller: Intel Corporation 82865G Integrated Graphics 
Controller (rev 02)" is what I get when I check my graphics card.

This is on my parents' PC, so getting a workable solution soon would be good to prevent any negative perceptions of Ubuntu. ;-)

---

### Post by zalberico on 2009-04-23
I have the same issue, something broke on the update with my integrated intel graphics and now no desktop effects.  I remember desktop effects not working immediately with the old version too though I had to install install xgl or something, but it's different now so I'm not sure what to do.

---

### Post by murderslastcrow on 2009-04-23
Yeah, zman. It was the same earlier, and all I had to do was install the package xserver-xgl, if I remember correctly.

Problem is, you can't do that now since it's been marked obsolete. I sure hope there's a better solution than reverting to an older driver.

---

### Post by murderslastcrow on 2009-04-23
However, for anyone who wants to revert to the older driver, simple instructions can be found on [this page]("https://wiki.ubuntu.com/ReinhardTartler/X/RevertingIntelDriverTo2.4").

Look underneath for a list to compare your driver to the ones that did or did not get fixed there. I'm going to try this out since mine is said to work with the older driver. I really don't have the time to wait for another solution just yet.

---

### Post by murderslastcrow on 2009-04-23
P.S. I ran compiz-check (script in the sticky on this forum) and got the following output.

"Gathering information about your system...

 Distribution:          Ubuntu 9.04
 Desktop environment:   GNOME
 Graphics chip:         Intel Corporation 82865G Integrated Graphics Controller (rev 02)
 Driver in use:         intel
 Rendering method:      None

Checking if it's possible to run Compiz on your system...  [SKIP]

 Checking for hardware/setup problems...           [SKIP]

At least one check had to be skipped:
 Error: No rendering method in use (AIGLX, Xgl or Nvidia)"

I have yet to revert the driver like I stated earlier.

---

### Post by murderslastcrow on 2009-04-23
K, after following the guid to revert to 2.4 drivers, everything's in working order again. Those notifications are actually quite pleasant. :3 I'm excited to see what new things the community will come up with.

P.S. They really should include a simple option to disable them, though, since I'm sure not everyone loves it as much as I do.

---

