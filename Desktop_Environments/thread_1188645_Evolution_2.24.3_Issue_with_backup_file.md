---
title: "Evolution 2.24.3 Issue with backup file"
date: 2009-06-15
forum: Desktop Environments
---

### Post by yackmaster on 2009-06-15
I just bought a Dell Insprion Laptop 15n (1545) ( Kernel 2.6.27-14-generic, GNOME 2.24.1)with Ubuntu 8.10 preinstalled to replace my Dell Latitude D610.  Everything on this unit is working perfectly out of the box except Evolution.  Here is what I've tried to do.

My old dell laptop is a Latitude D610 recently upgraded to 9.4 (Kernel 2.6.28-13generic, GNOME 2.26.1) and Evolution backup still is working fine as is the ability to send and receive email. I back up my email weekly. I thought I would be able to take my most recent Evolution back up file and import/restore this file in to Evolution on the 15n. When I did this I get the following error message.

"table inbox has 28 columns but 26 values were supplied" Just to be sure I've tried several other old back up files on the 15n and have gotten the same error message. 

Can anyone shed some light in to this issue? Is there an issues between versions?

Thanks in advance!

---

### Post by days_of_ruin on 2009-06-15
Try reading this: [https://bugs.edge.launchpad.net/ubuntu/+source/evolution/+bug/327057]("https://bugs.edge.launchpad.net/ubuntu/+source/evolution/+bug/327057")

---

### Post by yackmaster on 2009-06-16
FYI, This is now fixed. Thanks to "days_of_ruin" for the help. 

Rather than go in to what did not work I'll tell you what did. First I went through the whole thread "days_of_ruin" passed on. I tried all of the suggested fixes and the one that worked was to delete the "folders.db" file located at  "/.evolution/mail/local/folders.db*". Then I had to 'view' each folder (Inbox & the ones I created) in Evolution to reindex. This was essental in order to get my rules/filters to work correctly.

---

