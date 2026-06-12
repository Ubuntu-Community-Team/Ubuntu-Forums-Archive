---
title: "GNOME lock screen breaks sometimes in Ubuntu 18.10"
date: 2018-10-24
forum: Desktop Environments
---

### Post by jfjuneau on 2018-10-24
Hi,

Since I updated my laptop from Ubuntu 18.04 to 18.10 I have random issues with the lock screen. Sometimes when I press Alt+L, at first it looks like nothing happens. I can still see the desktop or the active window but I can't click on anything except the icons on the side panel. If I press Alt+L a second time, the lock screen finally appears, but I can still launch apps from the side bar. (screenshots in attachment) 

If I log out and log back in it solves the lock screen issue for some time before the bug reappears. Am I the only one with this bug?

Thanks!

JF

---

### Post by BadServo on 2018-10-25
I'm seeing the exact same behavior.  I have no idea what's causing it.  It seems to occur more frequently when I run web-based video in fullscreen, but it could just be a coincidence.  I also upgraded from 18.04 to 18.10.

---

### Post by jwtalbot on 2018-10-25
Same here

---

### Post by krvl on 2018-10-26
Experiencing similar on a laptop. When clicking *Lock* from the user icon in top right corner, the  selected menu starts flickering and stays that way until the lid is  closed. When opened again,  the usual login screen (with time) is  displayed. Please see attached screenshot.  Looks like the presence of connected external monitor does not affect  the issue. Happens only when locking from the menu, *Super+L* works fine.


Upgraded from 18.04 via cli on Thinkpad T450s. 

[ATTACH=CONFIG]281452[/ATTACH]

Please check this [bug on Launchpad]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1798615") and mark if it affects you too - this way there might be a quicker solution to the issue.

---

### Post by Plurtu on 2018-10-26
More relevant Launchpad bugs:

[gnome session: Must ask twice to lock the screen]("https://bugs.launchpad.net/ubuntu/+source/gnome-shell/+bug/1799293")

[Icon dock visible on lock screen]("https://bugs.launchpad.net/ubuntu/+source/mutter/+bug/1799430")

---

### Post by quillerszasza on 2018-11-15
Hi guys,
same here, with the exception that the upgrade from 18.04 died in my hands for some reason. I then installed 18.10 cleanly for my newly formatted partition, while my /home remained untouched (with some possible relevant settings).
I cannot find out what's triggering it, though. Seems like some gnome-shell binaries crash, from the syslogs ...

---

### Post by cybrsaylr on 2018-11-17
Having a similar lockup problem with 18.04 when switching users. Desktop completely locks up when switching users. Have to do hold down power button, doing a hard shutdown, to restart PC to get back running again.
Reported it in this thread and so far gotten no help.
Bionic Beaver 18.04 locks up when attempting to switch users [https://ubuntuforums.org/showthread.php?t=2403236](https://ubuntuforums.org/showthread.php?t=2403236)

---

### Post by g3charlotte on 2018-12-25
I get the same problem on a clean install of 18.10 on a Lenovo ThinkPad T430

---

### Post by skipperpl on 2019-01-05
Same, for me, Lenovo L480. 
What I see also, is the "dock" notification icons (Discord, Skype and other) disappear after Screen Lock "bug".

---

### Post by skipperpl on 2019-01-07
Hello All,

I found a solution for the flickering lock screen o the other forum:

Simply type in terminal
```
gsettings set org.gnome.shell.extensions.dash-to-dock transparency-mode FIXED
```

And all problems gone ;)

---

### Post by MiroJanosik on 2019-01-13
Call to gsettings does not solve anything for me, workaround that works for me is "sudo apt-get remove gnome-shell-extension-ubuntu-dock" (thanks to [https://github.com/micheleg/dash-to-dock/issues/649](https://github.com/micheleg/dash-to-dock/issues/649) )

---

### Post by g3charlotte on 2019-01-22
Not sure if it's been fixed or if I've just been lucky but I haven't had this problem recently.

---

