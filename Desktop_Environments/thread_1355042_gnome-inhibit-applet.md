---
title: "gnome-inhibit-applet"
date: 2009-12-14
forum: Desktop Environments
---

### Post by ForgivenByJC on 2009-12-14
I currently use gnome-inhibit-applet because MythTV and gnome-screensaver are having issues right now.  However, upon reboot the applet disappears, I add it again, and then reboot again and have 3 gnome-inhibit-applets running.  It seems the applet cannot survive a reboot, but if it does then it has several different applets.  What could this be?
Running:
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

$ apt-cache policy ubuntu-desktop 
ubuntu-desktop:
  Installed: 1.175
  Candidate: 1.175
  Version table:
 *** 1.175 0
        500 [http://archive.linux.duke.edu](http://archive.linux.duke.edu) karmic/main Packages
        100 /var/lib/dpkg/status

---

### Post by Perturbed Penguin on 2010-01-08
I have been having this issue as well. What happens is it will temporarily disappear from the panel for some reason. If you reboot though it will reappear without you doing anything, if you add another and then reboot it will likely show the original as well as the recently added applet. This is not a huge problem but I would also love to find a way to stop this from happening as I use that applet all the time when I do video editing or rip my DVDs where I want to be sure I can leave the computer for extended periods without it shutting down on me or anything of the sort.

---

### Post by ForgivenByJC on 2010-01-13
Nice nick, Perturbed Penguin.  A solution I stumbled upon was to enter```
gnome-panel --replace
```in the run dialog box (Alt-F2).  Unfortunately, I cannot enter it into gnome-terminal, because it becomes tied to it (even if run in background) and closes when gnome-terminal is closed.

The run dialog box (Alt-F2) does not work without gnome-panel running.  So, the work-around I use is to type```
gnome-panel --replace
```into gnome-terminal and then do so again in the run dialog box (Alt-F2) which unties it from gnome-terminal.

Does anyone know of a better way run gnome-panel --replace in gnome-terminal without gnome-panel and gnome-terminal being tied together?  The "&" afterward does not help.

---

### Post by Perturbed Penguin on 2010-01-16
That is a great temporary fix, thanks a bunch - I really hope they fix this little issue in Lucid though!

---

