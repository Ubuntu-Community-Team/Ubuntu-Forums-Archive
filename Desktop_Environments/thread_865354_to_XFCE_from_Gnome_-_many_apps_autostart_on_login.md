---
title: "to XFCE from Gnome - many apps autostart on login"
date: 2008-07-20
forum: Desktop Environments
---

### Post by moodog on 2008-07-20
I've been using gnome for a long time and finally decided to try XFCE so I installed the xubuntu-desktop package. It installed and ran, and to be honest I love it. The only problem was that the first few times I logged in and out, I inadvertently had the "Save Session on logout" (or whatever) checkbox checked. As a result, when I last (was able to) logged in about 6 skypes, 6 wicd's, and many other applications were opened. I found a link that said to delete stuff from  ~/Desktop/Autostart and ~/.config/autostart and ~/.cache/sessions/. I've tried this, but the applications are all still starting, so much so that I can't even get to the desktop at all - it gets part way through starting XFCE and then crashes, returning to the login screen. How can I stop the autostart of the apps? (assuming that is what's happening)

i was able to Ctrl-F2 to another terminal and run top, and found dozens of python processes (along with many other multiple instances)

---

### Post by moodog on 2008-07-21
anyone?

---

### Post by moodog on 2008-07-23
Hmmm... oooookay then. Given I liked XFCE but it won't work in it's current flavour, what's the best way to completely obliterate it so that I can reinstall it? I tried apt-get install --reinstall, but that didn't appear to solve the problem.

---

### Post by infinitejones on 2008-07-23
Have you tried logging into Gnome, and turning off autostart apps there? Or go into Sessions in the Preferences menu (again in Gnome) and make sure they don't all have entries there?

---

### Post by estyles on 2008-07-23
Rather than reinstall, try ```
apt-get remove --purge ...
```where '...' is the name of the package.  xubuntu-desktop, maybe?   Then install it again.  If it's a problem with xfce or its settings, that should kill it.  If not, then...  umm, I don't use xfce so I won't be much help.

---

### Post by jimmy the saint on 2008-07-23
The solution to this issue is here: [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

---

### Post by moodog on 2008-07-24
> **jimmy the saint said:**
> The solution to this issue is here: [http://ubuntuforums.org/showthread.php?t=854557](http://ubuntuforums.org/showthread.php?t=854557)

Sorry, but I can't find the solution here. I've tried unchecking the "Automatically save session on logout" and checking the "Prompt on logout" checkboxes, deleting the autostart and cache entries and the problem is not solved. Haven't had a chance to try purge and reinstall, but will see how that goes.

---

### Post by laxaman on 2008-11-04
Use xfce4-autostart-editor :p

---

