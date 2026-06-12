---
title: "[SOLVED] Programs fail to load"
date: 2009-01-08
forum: General Help
---

### Post by dotdot6 on 2009-01-08
Hi, I am new to Ubuntu(Windows user here).  I have played with Ubuntu in the past after failing to get my Radon graphics card to work correctly with it. I gave up on Ubuntu and going back to windows I was left disappointed as I really wanted to use  Linux as a dual boot system until I was more failure with a Linux based OS.  I now have since upgraded my computer and it now has a GForce 8600 GT graphics card (two are installed on SLI). I have since re-installed Ubuntu(Ultimate Edition 2.0) after two re-installs and hours of forum searching I manage to get the Graphic cards to work correctly and everything worked flawlessly until I had to reboot. After the reboot I found Firefox failed to load and gave me an access error I cant quite recall the error but one of the solutions was to delete a file in the profiles folder which did not work for me my solution was to delete the profile folder and the profile.ini file(may help others if needing a fix), so I just now manage to get that fixed which brings me to this point.

My problem...
Trying to load Compiz-Icon does not work, when I click it, it fails to load in the panel with the clock, (please note that cpmpiz-settings works fine, except it doesn't seem to save its settings but that might be for another thread), I have tried to load it with sessions manager and it still fails(have even tried other ways of getting it to start at startup and still fails), aMSN is also the same clicking it, it attempts to load, I see it on the taskbar but not in the panel next to the clock then it closes, it seems whatever app that uses the panel fails. The default applications that run in the panel with the clock at startup all works fine.

Prier to rebooting all applications worked fine and I had no issues and I have search many forums and found no solution.  If anyone could help me with my issues it would be greatly appreciated.

Main apps I need to get working is compiz-icon and aMsn.

Thank you.

---

### Post by gettinoriginal on 2009-01-10
Are you sure you have "notification area" applet on your panel ??

---

### Post by dotdot6 on 2009-01-10
Sorry yes I was sure but no problems any more after searching around I found out the the folders and some files were locked or more-so had my permission taken away so a simple chmod did the trick and now all is working as it should but thanks for your advice much appreciated.

---

