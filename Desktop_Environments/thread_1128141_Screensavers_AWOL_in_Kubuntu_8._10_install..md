---
title: "Screensavers AWOL in Kubuntu 8. 10 install."
date: 2009-04-17
forum: Desktop Environments
---

### Post by casbahdk on 2009-04-17
I just installed Kubuntu 8.10 on my Lenovo T60. For some weird reason the screensavers are AWOL. There isn't a single screensaver listed in the Desktop --> screensaver settings. Any ideas?

Cheers

---

### Post by JohnMoore on 2009-04-18
Start a package manager from Applications->System.

Use the search facility hunting for "screensaver" without the quotes.  See what's installed and what's available.

If there's no screensaver installed, try installing xscreensaver.  If there _is_ a screensaver installed, right-click the packages and uninstall them.  I prefer a complete removal for this, myself.  Once that's done, mark the packages for installation, and let the package manager put them back.

That should fix any installation glitch.

---

### Post by casbahdk on 2009-04-19
Thanks John. I tried installing Kubuntu 9.04 RC1 and the screensavers were also AWOL there. I did a "sudo aptitude install kscreensavers" and added some other screensavers at the same time.

Cheers,

---

