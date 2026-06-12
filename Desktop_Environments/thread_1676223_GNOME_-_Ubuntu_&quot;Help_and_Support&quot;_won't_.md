---
title: "GNOME - Ubuntu &quot;Help and Support&quot; won't start"
date: 2011-01-26
forum: Desktop Environments
---

### Post by nonquotidian on 2011-01-26
Hello Ubuntu Forums!

I've been running Ubuntu for a year or so, and I've found these forums very helpful - thank you for the support. 

I left this laptop for a while, and came back to it, so Ubuntu had come out with new versions. I upgraded step by step from 9.04 to 9.10 to 10.04. The upgrades returned no errors. But since I upgraded, I've been unable to open the System > Help and Support or the System > About Ubuntu. A tab on the bottom of the screen appears, saying "Starting Help and Support," and then goes away after 10 seconds. This doesn't change if I'm connected to the internet or not. 

Do you have any suggestions of ways I can troubleshoot this problem? Is there a way to try to launch the Help and Support from the command line? If that fails, what should my next step be?

Thanks in advance for your help,

nonquotidian

---

### Post by croakers64 on 2011-03-18
I have the exact same problem. I upgraded from 9.04 to 9.10 to 10.04 as you did. No other issues with the upgrades. Just can not open help and support or about Ubuntu. Anyone have any ideas?
Dana

---

### Post by croakers64 on 2011-03-18
Dug around and found a fix that worked for me. I went to /etc/gre.d . I had one system.conf.dpkg-bak file. It was an older version than reported installed by xulrunner in synaptic package manager. I tried reinstalling xulrunner but it still would not write the system.conf file to the folder. I downloaded the xulrunner deb package from [http://packages.ubuntu.com/lucid/i386/xulrunner-1.9.2/download](http://packages.ubuntu.com/lucid/i386/xulrunner-1.9.2/download)   .I then extracted the deb contents to a folder then extracted the data archive. I copied 1.9.2.15.system.conf from data/etc/gre.d to /etc/gre.d . I can now open about ubuntu and help and support with no problems. I deleted the old system.conf.dpkg-bak file also.
Dana

---

