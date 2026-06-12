---
title: "Adept Only Shows Installed Packages"
date: 2009-01-03
forum: General Help
---

### Post by randomidea on 2009-01-03
This is a thread for future reference. Check your updates tab in the edit software sources window.

I tried to install CinePaint, and wrote sudo aptitude install CinePaint in a terminal. The terminal did the usual matrix-looking thing, and I was presented with the (Y,n) option. Having installed and used CinePaint before on previous versions of Kubuntu (currently using 8.10), I chose y without question. Big mistake.

The terminal showed a bunch of packages being removed! Some of these included kmix, kscreensaver, knetwalk, etc. I had no clue why, so I scrolled up the terminal and read something along the lines of "CinePaint was not found, but the following packages mention CinePaint, and will be removed." Then I saw the list of packages, which was long, and I don't remember them, except that they all started with k.

I grimaced and rebooted, then opened adept to see if I could reverse the problem. But adept didn't show any of the packages I wanted to reinstall, and the fetch-list button resulted in a much shorter list of sources being checked than had previously been the case, and each source failed. I panicked, and turned to Google. To no avail! Even Ubuntu Forums didn't address my problem. I naturally checked my software sources, which were as they had always been (multiverse, universe, asf.)

I also checked to see whether my search was working. I typed in "gimp," which usually produces a giant list of available packages, but this time there were only about two dozen, and all of them were already installed! I checked the filter, and everything relevant was selected (installed packages, available packages, asf.) Crap!

Finally it occurred to me to check my update options. For some reason, the usual options were unchecked. I rechecked them, clicked okay, and hey presto, the package list was fetched and I had some upgrades! Everything is apparently back to normal.

---

### Post by randomidea on 2009-01-03
Update: my screensavers, which hadn't previously worked, are fixed. Woo-hoo!

---

