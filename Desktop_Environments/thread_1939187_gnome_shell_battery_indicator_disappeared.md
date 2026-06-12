---
title: "gnome shell: battery indicator disappeared"
date: 2012-03-11
forum: Desktop Environments
---

### Post by pille02 on 2012-03-11
Hi,
after some updates 2 days ago (including a kernel update) the battery indicator of the gnome shell disappeared. I installed an alternative indicator applet, this is neither showing up in the applet bar, while being activated in extended settings.

Has anyone an idea? Is this a problem due to the kernel update?

Thanks,
Philipp

---

### Post by whiskers751 on 2012-03-11
Well why not boot from an earlier kernel?

---

### Post by pille02 on 2012-03-11
I checked and it's not a kernel problem. Since the last updates, the icons in the applet bar seem to "overlap" each other. I deactivated some and the battery indicator was visible again.

I couldn't find any solution to this problem neither. Is it possible to resize the area for gnome shell applets? There is enough free space in the top bar...

---

### Post by Frogs Hair on 2012-03-11
I had a dual panel glitch last night and it was solved when I changed the wallpaper . What ever caused it occurred when I used appearance preferences to change the wall paper . When I selected a wallpaper from my pictures folder the secondary panel vanished.. It was strange because the time on the other panel was one hour earlier . I too received Gnome Shell updates last week .

---

### Post by arbrandes on 2012-03-27
I had this problem for a while, thinking it was a gnome-shell bug, but instead it was the [sytem-monitor extension]("http://www.webupd8.org/2011/10/gnome-shell-system-monitor-extension.html"),  which in its latest iteration (updated automatically from the webupd8 repo) offers an improved battery icon, and by default hides both the default system icon and the new one.

---

### Post by u2nTu on 2012-11-03
This long-standing bug remains a problem, even in current releases. (See the **[12.10 bug report]("https://bugs.launchpad.net/ubuntu/+source/gnome-session/+bug/1037676")**, the **[12.04 bug report]("https://bugs.launchpad.net/ubuntu/+source/indicator-power/+bug/997758")**, the **[11.04 bug report]("https://bugs.launchpad.net/ubuntu/+source/ubuntu-mono/+bug/801180")**,  or even the ... well, you get the idea.)

There is a simple work-around, but first, if battery indicator is  not visible, check that the daemon is running:```
ps -ef | grep  gnome-settings-daemon
``` should return lines something  like:> foo      1750  1309  0 15:12 ?        00:00:05  /usr/lib/gnome-settings-daemon/gnome-fallback-mount-helper
foo      20001     1  0 20:06 ?        00:00:00  /usr/lib/gnome-settings-daemon/gsd-printer (the  "gnome-fallback-mount-helper" line if logged into a GFB session).

If  no gnome-settings-daemon lines, first be sure the indicator is  installed and not corrupt:```
sudo apt-get purge indicator-power
sudo  apt-get install indicator-power
```Logout, back in and check again.  If still no gnome-settings-daemon, set gconfig:```
gsettings set  org.gnome.settings-daemon.plugins.power active true
```Now ready to  apply the work-around.



**WORK-AROUND**
First, test that  battery indicator can be forced to display without problems. When it's  not visible, run:```
killall gsd-printer
gnome-settings-daemon
ps -ef | grep gnome-settings-daemon
```See  that there is only one instance (one line) with "gsd-printer" and after  a display blink (more noticeable on older machines), the battery  indicator reappears.


Test again until satisfied that the method  works, then daemonize by pasting the following into gedit (or favorite  text editor) and saving as battery-indicator-temporary-workaround.sh  (for example) in ~/.local
```
#!/bin/bash

# Battery-indicator-temporary-workaround.sh
# For info, see: http://ubuntuforums.org/showpost.php?p=11797391&postcount=6
# This script is a temporary fix to keep the battery indicator visible. Remove when battery indicator no longer disappears.

while :; do
  killall gsd-printer
  gnome-settings-daemon
  sleep 10
done
exit 0
```Make  executable by clicking to allow execution on Permissions tab of  Properties dialog, or by:```
chmod +x  ~/.local/battery-indicator-temporary-workaround.sh
```If  satisfied that battery indicator disappears for a maximum of 10 seconds  (adjust 'sleep' as desired), set to auto-start in Applications | System  Tools | Preferences | Startup Applications (or search Startup in Dash if in  Unity).

Remember to watch for the disappearing behavior to  itself disappear when the source of the problem is corrected. Then this  fix-utility can be removed from Startup and deleted.


If this work-around is satisfactory, pille02, please mark this thread as 'solved'.

---

### Post by u2nTu on 2012-11-29
Quick update to note:

The flashing/blinking display in 12.10 got to be too much and I decided to let the rival programs battle it out on others' machines. Re-installed 12.04 -- problem solved. No more need for funky workarounds.

---

