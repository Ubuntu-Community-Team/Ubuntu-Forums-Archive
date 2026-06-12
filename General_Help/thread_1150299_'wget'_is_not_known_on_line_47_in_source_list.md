---
title: "'wget' is not known on line 47 in source list"
date: 2009-05-06
forum: General Help
---

### Post by Fozz on 2009-05-06
Help I'm a total n00b trying to run 9.04 inside a Sun Virtual 2.2.0 box on a Fujitsu laptop

Was following the directions in Comprehensive Multimedia & Video Howto and some how screwed it up now NONE of the package managers work I keep getting the error :

E: Type 'wget' is not known on line 47 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

from the Synaptic package manager and the update manager

Please remember I know little or nothing and am trying to convert away from MS. I'd like to fix the problem and NOT scrub this install

---

### Post by adult swim on 2009-05-06
press alt+f2 and enter in ```
gksu gedit /etc/apt/sources.list
``` and then look for the line that begins wget.  erase that line.  all of the lines in your sources list will either begin with deb or deb-src.  the save and close the file and try to update again.

---

### Post by Fozz on 2009-05-06
outstanding!!!!

 This worked. Thank you.  If you have the time would you explain what happened and how it was fixed so that I might learn something.

---

### Post by Zack McCool on 2009-05-06
To get specific, you could post a link to the HOWTO you were using, but my guess would be that you were following the directions step-by-step, and missed a step.

Basically, the HOWTO had you manually edit sources.list and add some lines, then it instructed you to do a wget to download something (probably a GPG key).  What you missed in between was the part where you were to save and exit sources.list...   ;)

It's a simple mistake, and could happen to anyone...   Well, not ME, but anyone else...   ;)

---

