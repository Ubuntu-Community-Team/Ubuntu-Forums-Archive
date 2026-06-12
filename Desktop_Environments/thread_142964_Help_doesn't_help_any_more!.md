---
title: "Help doesn't help any more!"
date: 2006-03-11
forum: Desktop Environments
---

### Post by gskey on 2006-03-11
When selecting the Help option (via the System option then Help) the Help window displays but none of the option links appear under Help Topics. When I click on the icon Help Topics within the window absolutely nothing happens. Prior to this the Update Manager updated the kernel and some other applications/libraries but nothing to do with the help program 'yelp'. Anyway, I reinstalled the yelp program but still no success. Has anyone encountered this problem? If so, how do I get the Help feature to work? This problem does not occur if I boot the Ubuntu Live version from CD, only when I boot the installed version from the hard drive. Any help/suggestions will be appreciated.

---

### Post by flanagan on 2006-03-12
FWIW, Help does not work for me either since the last kernel update. Mine does not even display a help window, though, so in that sense the bug displays itself differently. On my machine, it spins for a few seconds and silently disappears.

I'll do some research and post back if I find something about this.

---

### Post by flanagan on 2006-03-12
I don't know if this helps your problem, but yelp did not stop working for me because of the last kernel update. It broke when I upgraded to Firefox 1.5.0.1 (at about the same time).

Yelp evidently relies on Firefox, and it seems only satisfied with the older 1.0.7 version typically found in /usr/lib/mozilla-firefox. I have fixed my problem by maintaining two versions of Firefox: the old 1.0.7 in /usr/lib/mozilla-firefox AND version 1.5.0.1, the one I use regularly, in /opt/firefox (for instance).

---

### Post by ronmarley1 on 2006-03-12
Hmmmmm.  I have FF 1.5.0.1 and yelp works fine.  I remember reading something related to this about installing FF with Automatix and breaking yelp.  However, I'm not postitive...

---

### Post by flanagan on 2006-03-12
If you completely replace the Firefox 1.0.7 that came with Breezy, Yelp will cease to function. To solve this, I installed FF 1.5.0.1 in a separate folder then relinked according to the instructions at [FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion). This leaves the FF 1.0.7 intact in /usr/lib/mozilla-firefox for the use of several applications that look there (hard-coded evidently) for the Gecko rendering engine. The preceding link lists Yelp among a few other applications that require the original Gecko engine that came with the Breezy release.

---

### Post by gskey on 2006-03-13
Thanks to all of you who responded. I'm going follow the suggestions given and hopefully that will solve the problem. I'll let you know the results.

---

