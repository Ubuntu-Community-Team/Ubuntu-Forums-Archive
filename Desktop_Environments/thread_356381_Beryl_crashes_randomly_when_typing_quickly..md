---
title: "Beryl crashes randomly when typing quickly."
date: 2007-02-08
forum: Desktop Environments
---

### Post by copilot on 2007-02-08
I've been experiencing some xgl crashes since installing beryl using the guide on their wiki. I'm hoping someone might have had the same problem. Beryl starts and runs great but crashes randomly if I'm typing quickly. It sometimes returns to the login screen but other times requires me to restart x to get away from the blank screen. I'll try and get a screenshot of it after it crashes. I found a bug report for an older version of beryl but no solution.

beryl-core 0.2.0-svn installed via [this guide.]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Dapper_with_XGL") I'm running a Pentium D 2.8 ghz and an nVidia GeForce 6200. I can post any additional info that would help, but I'm not sure where to get log files or error messages since none are presented during the crash.

---

### Post by Robor on 2007-02-08
I noticed that I was having GDM crashes when typing quickly and it happened most often when I was trying to backspace.  I was accidentally holding down the shift key sometimes and shift-backspace restarted X.  I disabled that command - can't remember the method but if you Google I'm sure it will come up easily.  I have had a few other GDM crashes when typing very quickly so I've probably got the same issue you have.  Hopefully it will be fixed in a future release.  I'm going to go apt update/upgrade now.  :)

Edit:  Looks like there's some updates for Beryl as well as a kernel update.

---

### Post by glxyjones on 2007-03-26
I am experiencing the same issue.  Have you found any solution for it?  I do not know if it is because I am accidentally entering a command that causes Beryl to exit and enter the login screen or if just simply typing too fast crashes it.  I have the lastest Beryl and Ubuntu updates installed.

---

### Post by rnwld999 on 2007-04-09
This worked for me:

[http://www.vishalarya.net/?p=229](http://www.vishalarya.net/?p=229)

Add this to the System ->Preferences ->Sessions ->Startup Programs:

    “xmodmap /usr/share/xmodmap/xmodmap.us”

---

