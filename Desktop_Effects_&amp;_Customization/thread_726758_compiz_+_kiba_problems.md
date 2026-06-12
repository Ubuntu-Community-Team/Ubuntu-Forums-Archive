---
title: "compiz + kiba problems"
date: 2008-03-17
forum: Desktop Effects &amp; Customization
---

### Post by ac3raven on 2008-03-17
I installed kiba dock, and compiz stopped working, I uninstalled compiz and ccsm then reinstalled it, but that didn't help.  this is what happens when I try to open ccsm from the terminal:

glenn@starbuck:~$ ccsm
Traceback (most recent call last):
  File "/usr/bin/ccsm", line 45, in <module>
    idle = ccm.IdleSettingsParser(context)
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 229, in __init__
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 228, in <lambda>
  File "usr/lib/python2.5/site-packages/ccm/Utils.py", line 225, in FilterPlugin
AttributeError: 'compizconfig.Plugin' object has no attribute 'Initialized'
glenn@starbuck:~$ 

the same result when I am root.  Compiz seems to be installed properly and everything, I just can't open it and none of my custom preferences (cube, rain etc..) are working.

---

### Post by ebharv on 2008-03-17
You and I must be the only two people with this problem. I even went as far as removing Kiba and CCSM then reinstalling CCSM and still nothing. I'm at a loss. Part of what made Ubuntu so much fun to work with is Compiz. I organize my work when my desktop get cluttered just to see it's eye candy. It's amazing how much more productive I am in Ubuntu than WinXP. 

Can anyone help pppplllleeeeaasssee????!!!!!:confused:

---

### Post by ac3raven on 2008-03-17
I FOUND THE FIX, let me find the link again and I'll post it!! W00t!

---

### Post by ac3raven on 2008-03-17
okay, having trouble finding the link, but in the mean time, go to your sources.lst (or just go to your software sources via gui) and get rid of the the tuxfamily repositories.  then completely remove compiz and all of it's components including ccsm, then reinstall it via synaptic.

---

### Post by ac3raven on 2008-03-17
[http://forum.compiz-fusion.org/showthread.php?p=47146](http://forum.compiz-fusion.org/showthread.php?p=47146)

exerpt:
"Okay, you can keep all the packages whose version string ends in "~gutsy1" or "ubuntu#", but all the packages whose versions end in "3v1ubuntu0" have to be removed. The official packages from Gutsy and the gutsy-backports repository are based on the stable release version of Compiz, which are not compatible with Trevino's old snapshots of Compiz Fusion from git. Trevino's repository is also currently unmaintained, so its packages contain known problems that are unlikely to be fixed."

that fixed it for me.

---

### Post by ac3raven on 2008-03-17
oh, and I got rid of kiba and avant before doing all this.

---

### Post by ebharv on 2008-03-18
Thanx, I'll try it when I get home.

---

### Post by ebharv on 2008-03-20
Did the fix and everything is back. And I didn't have to uninstall Kiba-Dock. I did have to reinstall compiz-gnome though. Thanks for finding the fix

---

