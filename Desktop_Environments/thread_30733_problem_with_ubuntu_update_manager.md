---
title: "problem with ubuntu update manager"
date: 2005-04-30
forum: Desktop Environments
---

### Post by nojjy on 2005-04-30
So Update Manager has recently informed me that openoffice.ore-l10n-en, openoffice.org.thesaurus-en-us, and ttf-opensymbol have upgrades available.  OK fine, I click install, the program greys out for a second and then un-greys.  That's it.  The updates are still listed and the console doesn't report any errors.  Does anyone have any guess to what's going on?

---

### Post by 23meg on 2005-04-30
check your repositories to make sure you have all sections enabled in "updates" and "security updates", and see if typing "sudo apt-get update" helps you.

---

### Post by nojjy on 2005-04-30
Your suggestion led me to a solution, thanks.  I had to uncomment these lines from sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

Just thought it strange of myself that I uncommented everything else before but these.  Thanks!

Jon

---

### Post by 23meg on 2005-04-30
it's weird that update manager notified you of updates while you had these commented.. no probs if you got it working, though ;)

regards

---

