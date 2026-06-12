---
title: "Fixes for potentially common issues..."
date: 2005-11-06
forum: Desktop Environments
---

### Post by bdwalton on 2005-11-06
Hi All,

I've recently installed Breezy on my wife's machine at home (my machine is still on Sid) and I've had a few issues that I've solved and I'd like to share.  Some of these are Breezy issues, and others are simply network integration issues...none-the-less, I hope others can benefit from my experiences...I also hope this is the appropriate forum for posting these types of things.

Also, I don't claim that these are by any means the best way of solving the problems.

1. LDAP logins from GDM weren't working.  I have an LDAP server that I authenticate all users against in my network.  After configuring the required nss and pam settings, I could login from the console but not from gdm.  I discovered that this is due to the boot order of 2 services.  GDM was loading before nscd.  Swiching this boot order solved my login issues for gdm.  I haven't filed a bug about this yet as I haven't found the appropriate place...can someone point me to the right spot.  This is very reproducible and I can provide any logs necessary to help resolve in the future.

2. When I first installed Breezy, I was getting the HAL failed to initialize error that I've seen around a few other posts.  None of the posted solutions worked for me (eg: cd in drive at boot, etc).  The error has since stopped popping up (not sure when as my wife didn't tell me), but automounting of cd's and usb drives still wasn't working.  Today I discovered that a restart of the dbus service would restore working functionality for hal and my removable media and drives now automount correctly.  To make this a permanent fix, I created an init script in /etc/init.d called local.  I symlinked S99local in /etc/rc2.d to that script.  The content of the script was simply:

#!/bin/bash
/etc/init.d/dbus restart

This is one of the last init scripts run and on boot, my users now get working hal functionality from within gnome.  I'm not a fan of this solution, as it is definitely a kludge, but it does work for me...

3. My home directories are mounted over nfs from my main machine which works fine except for one thing.  OpenOffice.org 2(beta) and evolution were throwing all sorts of weird errors when trying to save files.  Other apps had no issues.  Both of the problem apps were trying to lock files.  I discovered that lockd on my main machine wasn't running and it wouldn't start.  This machine is Sid, btw.  I switched from nfs-user-server to nfs-kernel-server and enabled lockd in /etc/default/nfs-common and this problem dissappeared.  This is not an ubuntu problem, but is something that may affect other ubuntu users...

4. My wife's machine is older and still has an ISA bus with an ESS Solo sound card.  The alsa module setup wasn't working for it until I added snd-es18xx to /etc/modules to automatically load the module at boot.

Other than those 4 issues (some of which are not ubuntu's problems), I've simply fallen in love with this distro!

Hope my experiences can help others solve their problems a little quicker.  :p 

-Ben

---

### Post by NewWithoutClue on 2005-11-06
Although I have not run in to any of these problems, I thank you.

w00t,
Paul.

---

