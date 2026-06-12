---
title: "Compiz-core package broken?"
date: 2006-09-04
forum: Desktop Environments
---

### Post by richardq on 2006-09-04
After seeing the notifier for some new compiz related upgrades, it seems like the compiz-core package is breaking my system. No Compiz goodness right now, and I can't seem to figure out how to solve the problem.

Synaptic generates the following message:

E: /var/cache/apt/archives/compiz-core_0.0.13.44-0ubuntu1_i386.deb: trying to overwrite `/usr/bin/compiz-start', which is also in package compiz-quinn-aiglx

So compiz-core won't upgrade to the 13.44 version which is required for the rest of the compiz related package upgrades. Can anybody shed any light on this? I've tried sudo apt-get -f install compiz-core to no avail as well.

I haven't been able to find any similar recent messages from anyone either. Any help would be appreciated.

---

### Post by Uncle Spellbinder on 2006-09-04
Don't know if this will help or not but I uninstalled/removed compiz-quinn-aiglx a while back then did *sudo apt-get clean*. It's old and no longer used. After that, updates were no problem.

---

### Post by richardq on 2006-09-04
I finally fixed it. I ended up uninstalling all compiz related packages via Synaptic and then re-installing the quinn compiz packages again. Then of course it was dog-slow until I found this thread ([http://ubuntuforums.org/showthread.php?t=250489](http://ubuntuforums.org/showthread.php?t=250489)) about using csm to get the settings right. It defaults to use the blur effect which just kills my normally snappy system.

I disabled the icon in the desktop tray since it only gave a few settings to adjust. Using csm let me set everything I had before, but with a much nicer interface.

All is good once again.

Phew.

---

