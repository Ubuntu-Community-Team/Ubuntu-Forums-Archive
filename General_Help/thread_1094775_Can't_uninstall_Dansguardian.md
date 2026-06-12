---
title: "Can't uninstall Dansguardian"
date: 2009-03-12
forum: General Help
---

### Post by arthritisankle on 2009-03-12
I installed Dansguardian, firehol and tinyproxy per this howto: [http://ubuntuforums.org/showthread.php?t=207008](http://ubuntuforums.org/showthread.php?t=207008)

The filtering worked properly, but I could no longer use ushare to stream to my xbox360.  I tried to uninstall all three of them (with synaptic) to get things back to the way they were, but then I couldn't get on the internet at all.  I had to reinstall everything just to get to the forums.

Any ideas?

---

### Post by Hobgoblin on 2009-03-12
Did you undo...

> **tonhou said:**
> 
**In Firefox:**
Edit -> Preferences -> General -> Connection Settings -> Manual proxy configuration

Check manual proxy configuration and add “your DG box ip address” in first box and “8080” in second
Then tick “Use this proxy server for all protocols”

...after uninstalling?

---

### Post by arthritisankle on 2009-03-12
I seem to have fixed it now.  This time I checked "Mark for Removal" instead of "Mark for Complete Removal" in Synaptic and everything seems to be working fine after a reboot. 

thanks for the help anyway  :D

---

