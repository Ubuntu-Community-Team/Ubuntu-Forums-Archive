---
title: "How to use environment variables with unity launcher applications"
date: 2013-06-16
forum: Desktop Environments
---

### Post by RogerTa on 2013-06-16
Hi all,

How do I use the value of environment variables inside Unity launcher application items?  I have found several web pages explaining how to use "env" to set a variable, but I don't want to change anything, I just want to use an existing variable.

Use case: I run Google Chrome to browse the web and have its icon locked to the launcher.  I also remotely access my machine with nx.  If I leave Chrome running on the local desktop and start an nx remote desktop session, then clicking the Chrome launcher icon from inside the nx session causes a new window to appear on the local desktop.  This has to do with the way that Chrome detects if an instance is already running.  A "simple" fix would to change the Exec line in the google-chrome.desktop file:

From: ```
Exec=/opt/google/chrome/google-chrome %U
```
To: ```
Exec=/opt/google/chrome/google-chrome --user-data-dir=.config/google-chrome/$DISPLAY %U
```

where $DISPLAY is the X Windows display environment variable.  However, the Unity launcher does not expand $DISPLAY.  Am I doing something wrong?  Is there a better way to achieve my goal?  Thanks!

My system:

```
$ uname -a
Linux Chlorine 3.5.0-34-generic #55~precise1-Ubuntu SMP Fri Jun 7 16:25:50 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux
$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.2 LTS"

```

---

