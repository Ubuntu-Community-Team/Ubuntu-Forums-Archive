---
title: "Optiplex SX260 -- Gotchas?"
date: 2009-04-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by shinji257 on 2009-04-11
I am working on installing Ubuntu 8.10 to a Dell Optiplex SX260 that I acquired recently.  Other than the Compiz/X-Server issue is there anything else that I should be watching for?

P.S. - I would seriously like to see the 845G video driver issue fixed if that is indeed what is causing it.  I am willing to test them.

EDIT: It appears that Xubuntu does not have this issue.  I believe it is the fact that it doesn't install Compiz at all.  Compiz isn't a real loss to _me_ since I will be using it as a server unit more than anything.  The gui is just a plus to me.  I would still like to see the driver fixed.

EDIT: Well either no one knows anything additional here or doesn't want to help.  Granted this is an otherwise very helpful community.  Guess I should of known better asking about a 6 year old computer but I'll give my feedback here.  Everything appeared to work.  The line jack vs the headphone jack seems to have a few detection issues.  Ethernet was picked up without issue and used the e1000 driver.  For now the machine has been switched back to XP for other reasons.

EDIT: 9.04 Ubuntu worked fine out of the box granted the desktop effects can't be turned on.  I'll need to see if enabling the frame buffer will be ok with the desktop version.  The hot-swappable drive bay causes the system to hard lock if you eject it without releasing it from the system.  There is a work around but it needs to be thoroughly tested.  I need a hard drive bay for that slot and is compatible with my system first.  I have tested it with swapping optical drives though.  Also it seems that it won't see the floppy drive when inserted into that bay.  Don't know why.

---

### Post by boams on 2009-08-06
Hi Shinji,
 
I can certainly add feedback to this thread...
 
I myself own a Dell SX260 - I never really got too excited when I bought it anyway as I knew it was a few years old... but for £30 I couldnt complain. It seems fairly ok running Ubuntu, again the same as you there are a couple of annoyances I'm yet to figure out...
 
1) Same as you - I can't get Compiz to work properly, I can install Compiz fine, am able to access the Config Manager. However when I come to try and enable the Effects in Appearance I get an error message saying ' unable to apply desktop settings'.
 
2) My NIC goes to sleep - If I connect to Ubuntu from a Windows Desktop via VNC and leave it active for an hour. The Ubuntu machine's network will lock and to re-activate it - I have to reboot Ubuntu...
 
If I here of any drivers out there for us for the Graphics issue, I will be sure to post...
 
All the best :)

---

