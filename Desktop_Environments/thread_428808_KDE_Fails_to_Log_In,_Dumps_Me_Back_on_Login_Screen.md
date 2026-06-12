---
title: "KDE Fails to Log In, Dumps Me Back on Login Screen"
date: 2007-04-30
forum: Desktop Environments
---

### Post by tripinva on 2007-04-30
Please help! I can't get my GUI to open!

Yesterday I decided that I would switch from Azureus to KTorrent, since Azureus was sucking up memory like a tornado sucking up feathers, and so once I got it all configured and running, the program would randomly crash. Upon investigating this issue, I found that the resolution was to install a new version available from the KTorrent website. I did so with no issue.

Upon returning home from school today, after the system had been working just fine the evening/morning before, the system was now not letting me into the Konsole. KDE-Init was apologizing for being unable to launch it. I felt the next step would be a reboot, and upon doing so, the system now will not let me into the GUI. It boots just fine to the graphical login screen, but once I input my user name and password, the screen goes black as though logging in, then returns me to the login screen.

I tried running apt-get install kde from the command line and found a few missing packages, but this did not resolve the issue. An fsck also didn't help.

I'm not even sure where to look to get the correct log files to try and figure out what happened. Please help!

Thanks.

- Trip

PS - I've also posted about it on Questions for Ubuntu as well; I really need to get this resolved--I have work to do!

---

### Post by taurus on 2007-04-30
Any chance you are running out of disk space?  At the GUI login screen, KDM, press <Ctrl><Alt>F2 and log in with your username and password.  Then, run this command to see your disk space, especially the / one.

```
df -h
```

---

### Post by tripinva on 2007-04-30
Yes, that was it.  Why it didn't pop up some kind of message for me instead of just failing to log in, I have no idea.

Thanks.

- Trip

---

### Post by taurus on 2007-04-30
Clean up the archives with

```
sudo aptitude clean
df -h
```

---

