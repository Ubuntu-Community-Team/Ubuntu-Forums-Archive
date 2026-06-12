---
title: "Firefox 1.5 to Breezy repository?"
date: 2005-12-02
forum: Desktop Environments
---

### Post by teerik on 2005-12-02
Ok, there's plenty of FF1.5 threads already but I couldn't find any discussion about this.. I'm curious is the firefox package going to be upgraded to v1.5 in Breezy repository or should I just use the .tar.gz from the mozilla.org? And naturally eager to know about the schedule if it's going to be available for Breezy.

It's just nice to have all stuff installed with apt.. it's still no problem for me to use sources either. It's all about how long would I need to wait for it if not installing it by hand. Thanks in advance..

---

### Post by pertti on 2005-12-02
FireFox 1.5 will be available through the breezy backports, but not the normal repositories. However, in [this discussion]("http://www.ubuntuforums.org/showthread.php?t=96595") on the backports forums it's said that the backport is going to take a while, because there're a lot of packages that depend on FireFox.

I couldn't wait :), so I followed [these instructions]("https://wiki.ubuntu.com/FirefoxNewVersion") on the Ubuntu wiki, and now I have 1.5 running with mplayer and java plugins, and without any problem.

---

### Post by eeried on 2005-12-02
[Q]t's still no problem for me to use sources either[/Q]

Mozilla files are binaries -- so you only need to untar them, teerik.

I installed Firefox from the Mozilla Web site into /opt. You only need to disable both extensions that are shipped with Firefox 1.5 in order not to get a message about "a failure in chrome registration" after launching Firefox.

The Ubuntu Wiki says Firefox is faster this way than installing the Ubuntu package.

---

### Post by mrmcctt on 2005-12-02
I used the wiki listed above and everything worked perfectly.  I did this on blind faith and a lot of cut-n-paste (for the commands) and everything has worked perfectly.

I ignored one of the commands (the remove Totem plug-in) and I did get errors on Firefox start up.  I removed the Totem plugin and no more issues.

---

