---
title: "Downgrade"
date: 2009-01-29
forum: General Help
---

### Post by RedSingularity on 2009-01-29
Hey guys, i was wondering if it is possible to downgrade a release of linux?  For example from Ubuntu 8.10 back to 8.04.

---

### Post by dcstar on 2009-01-29
> **Shadow121 said:**
> Hey guys, i was wondering if it is possible to downgrade a release of linux?  For example from Ubuntu 8.10 back to 8.04.

Move your /home to a separate partition and it is easy (search for detailed instructions).

You will start again with a "normal" system again but your user config will still be there - but you will have to re-install any non-standard packages.

---

### Post by bumanie on 2009-01-29
It is not possible to downgrade from one distro. version to an earlier one. You have to reinstall. If you do this, as said above, copy /home somewhere, or at least copy any files you wish to keep first. If you already have aseparate /home, you only have to reinstall to / - you have to choose manual at the partitioning stage to do this. In fact a separate /home has the advantage that if you need to do something like you are doing, or your / filesystem gets wrecked, data in home is safe and you only need to reinstall to / If you reinstall, I would look at setting up a separate / ; /home ; swap if I were you, but you can do it however you feel most comfortable.

---

### Post by Slim Odds on 2009-01-29
Did you do any research before you posted this?

This has been asked and answered millions of times......

---

