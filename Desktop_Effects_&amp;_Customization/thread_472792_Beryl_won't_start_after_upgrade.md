---
title: "Beryl won't start after upgrade"
date: 2007-06-13
forum: Desktop Effects &amp; Customization
---

### Post by barnjo on 2007-06-13
I had a stable version of Beryl installed from Ubuntu repos.

I have just added Trevino's Fiesty eyecandy repos and upgraded all the beryl packages installed on my computer. It came up with an error to do with my cache when installing but running 'sudo apt-get upgrade' again seemed to do the trick.

After all this Beryl no longer starts. It just defaults back to Metacity. Interestingly beryl-manager will still start Compiz, and I upgraded those packages from Trevinos repository at the same time.

Running beryl from the command line gives a 'segmentation fault' error just after its tried to load the splash screen.

Anyone know how to fix this?

Thanks

---

### Post by sailor2001 on 2007-06-13
seems to be a small bug in the manager. Quite often (not all the time) I have to go from metacity to compiz and then to beryl in steps.... and even then it not always works the first time.

---

