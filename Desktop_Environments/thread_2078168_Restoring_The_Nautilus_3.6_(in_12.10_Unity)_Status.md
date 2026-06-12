---
title: "Restoring The Nautilus 3.6 (in 12.10 Unity) Status Bar"
date: 2012-10-30
forum: Desktop Environments
---

### Post by Mad-Halfling on 2012-10-30
Can I get the status bar back on Nautilus by poking around in a config file, somewhere, or is it completely removed and I need to revert back to an older version in the package manager?  I've looked in the new cog-icon preferences menu, but I can't see any options to turn it back on.  I thought losing it was going to be a minor inconvenience but it's an absolute nightmare and I keep having to switch to a terminal and execute df -h =8/

---

### Post by ryanwolf74 on 2012-10-31
I believe it was removed. Why did you even upgrade such a major package? They had reverted it and it has bad criticism for a reason, lol

---

### Post by OzzyFrank on 2012-10-31
I upgraded Nautilus to 3.6.1 (only because the 12.10 upgrade actually removed Nautilus altogether! So I added the PPA and ended up with the latest version), and I too miss the status bar, mostly because it always showed the free space remaining on the drive you're looking at. Having to right-click and open *Properties* just to see how much space is remaining is a real drag. I'd be happy if there is a hack to include that info in the "floating status bar", along with the info of the selected file(s). Yeah, sure, you'd have to select something just so the floating status bar appears, but if it included the free space of the drive/partition, it would still be easier than opening *Properties* every time. If anyone knows of a config setting to alter/add, please let us know!

---

### Post by Isamu715 on 2012-11-01
You can just go back to Nautilus 3.4 to regain that functionality. Uninstall Nautilus 3.6, remove the ppa and install Nautilus 3.4 from the default Ubuntu 12.10 repos.

---

