---
title: "Monitor does not power off"
date: 2011-11-07
forum: Desktop Environments
---

### Post by hbj on 2011-11-07
I am running the KDE desktop.  After upgrading to 11.10, I cannot get my monitor to automatically power off after a period of time.  It was working fine under 11.04.  I suspect something wrong with the settings after the upgrade but nothing I try makes it work.

I added "xset dpms" in an Autostart script, and xdpyinfo shows DPMS enabled.  In Power Management, the "Screen Energy Saving" is checked.  The screensaver comes on after the specified period but the monitors never power off.  What else can I try?

---

### Post by hbj on 2011-11-13
well, I seem to have fixed it somehow.  I searched my .kde folder for anything with the word screensaver in it, and then I deleted that config file.  I think there were two files.  It looks like there was maybe a config file disabling the screensaver.  After removing the file and logging out and back in, it monitor powers off as expected.

---

### Post by mister_playboy on 2011-11-16
You can mark this thread as SOLVED by editing the first post. ):P

---

### Post by hbj on 2011-11-16
Thanks for the tip but unfortunately the problem came back.  It worked for a day or two, now the monitors don't power off again, I don't think I actually changed anything to make it stop working, and I can't find anything else to make it work again.  I'm back to physically powering off the monitors.  I never had this problem in previous Ubuntu releases.  Any other suggestions are welcome.

---

### Post by mister_playboy on 2011-11-16
Have you already looked at the screen shut off settings under Applications > Settings > System Settings > Power Management?

---

### Post by hbj on 2011-11-16
Those settings appear to have to effect.  I wonder if its related, but if I try xset dpms force, the monitors suspend for a second but then come back on.  Something in kde is keeping the dpms from activating.  Is this powerdevil?  I have the performance profile.  I also have the power settings telling it to power off the screen after 10 minutes.  I tried disabling the screensaver but it still doesn't power off the monitors.

---

### Post by hbj on 2012-01-30
I am still having problems with this.  I wonder if it is perhaps related to GNOME applications.  I wonder if it is related somehow to this issue:

[http://ubuntuforums.org/showthread.php?t=1767146]("http://ubuntuforums.org/showthread.php?t=1767146")

I have the same problem that the GNOME background flashes when coming out of a locked KDE desktop.  I run Dropbox and some other GNOME applications, and I wonder if they are somehow messing with monitor power settings.

---

