---
title: "CPU use with udevd at 30-40%"
date: 2009-05-19
forum: General Help
---

### Post by MysticGold04 on 2009-05-19
Anyone else having this issue?  Since a recent update, probably a couple weeks ago, I've been having an issue with the udevd daemon eating 30-40% of my cpu just idling.  If I stop the daemon, the CPU use backs down to 1-2%.  Any ideas?  I tried the suggestions in this other thread, but don't seem to have an impact... would an issue with ext4 cause this?  

[http://ubuntuforums.org/showthread.php?t=1154175](http://ubuntuforums.org/showthread.php?t=1154175)

I attempted to upgrade to Jaunty, but the upgrade had issues with some manually installed packages and other repos I had, so I ended up doing a clean install to / as ext4, but kept my /home partition at ext3, and has been running great since the install, but up until just recently did I notice that my idle CPU was churning at 30-40%.

---

### Post by Soul-Sing on 2009-05-19
do you run conky?

---

### Post by MysticGold04 on 2009-05-19
Yep, sure do.. that's how I noticed that the cores were running at 30-40% and that udevd was one of the top processes.  I have also ran top and htop to verify what I have been seeing.

---

### Post by Soul-Sing on 2009-05-19
could you disable/uninstall conky? ( there are indications that conky causes these problems)
you can easily backup your conky script...

---

### Post by MysticGold04 on 2009-05-19
Conky causes issues with the udevd daemon?  

I start conky manually, so even when it is not running I still see the cpu use at 30-40% even by top, htop and system-monitor.  I definately don't think conky is the issue.

Edit: I should point out that my laptop is the issue, (running Jaunty) not my desktop (Vaio) I am running conky 24x7 on the Vaio running Hardy and have no issues.

---

### Post by MysticGold04 on 2009-05-23
Bump... anyone else having the same issue recently???

---

### Post by MysticGold04 on 2009-05-25
anyone else having an issue with udevd eating CPU use?  I really hate to have to re-install, because I have everything now as I'd like it.

---

### Post by MysticGold04 on 2009-05-28
I figured out how to force the previous version of udev back on my laptop from the Package Manager.  Issue solved for now, except I have an updates icon that is persistent, wanting me to install the new version of udev :)

---

