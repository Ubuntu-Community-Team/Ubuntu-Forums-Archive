---
title: "PureFTPd Initialization / Ubuntu Boot Sequence"
date: 2009-03-22
forum: General Help
---

### Post by kinsei on 2009-03-22
I have installed pureFTPd on my Ubuntu 8.10 installation and have everything working to my liking but one thing is driving me crazy.

I can't seem to find where the program is being called from upon bootup.  I would like to find out where this is since there are many switches that can be used as options during its initialization.  The readme files for pureFTPd suggest that a call from inted.conf or xinetd.conf are typically what starts the program unless it is running in standalone.  I do not have an xinetd.conf file and my inted.conf file only has one line and it's unrelated to FTP.

If I restart my machine FTP is working when it comes back up without any changes so it has to be called from somewhere.  I did try a couple of other programs first before trying pure ftpd so maybe its some sort of leftover remnant.  Can someone help me locate where the process is being started from in the boot sequence?

---

