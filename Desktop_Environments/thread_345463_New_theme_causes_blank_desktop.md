---
title: "New theme causes blank desktop"
date: 2007-01-24
forum: Desktop Environments
---

### Post by ews07 on 2007-01-24
After selected a new theme from the Theme Manager (System > Preferences > Theme) my desktop went blank.  I could still see the desktop background and the applications that were running at the time (Firefox and Terminal window), but the toolbar at the top with "Applications", "Places", and "System" is invisible.  When I restart Ubuntu I get the splash screen but no icons display.  I can hear the startup music but that's it.

I am able to get to command line by hitting Ctrl + Alt + F1 and toggle back to desktop with Ctrl + Alt + F7.  Is there anyway I can restore the files that Theme Manager updated?  I'm wondering if restoring gdm.conf or gdm.conf-custom would help?

Any help on which files I should restore and how to do the restore would be much appreciated.

Prior to this problem Ubuntu was running perfectly.  I am using:
- Ubuntu 6.10
- Dell Latitude C840
- 1 GB RAM
- 18 GB Harddrive (partition for Ubuntu)

Thanks - ews07

---

### Post by ews07 on 2007-01-24
I was able to solve this problem by following the resolution in this post:  [http://ubuntuforums.org/showthread.php?t=333090](http://ubuntuforums.org/showthread.php?t=333090).  

Specifically, I renamed the following folders: ~/.gnome, ~/.gnome2, ~/.gconf, ~/.gconfd, ~/.metacity while at the command line.  I got to the command line by doing Ctrl+Alt+F1.  Then logged in, did "cd /home/[username]".  Then did "mv .gnome .gnome.old" etc, for each file in turn.  Then rebooted system and all worked again.

---

