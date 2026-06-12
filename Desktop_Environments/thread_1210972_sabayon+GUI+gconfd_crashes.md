---
title: "sabayon+GUI+gconfd crashes"
date: 2009-07-12
forum: Desktop Environments
---

### Post by doom3d on 2009-07-12
Hi,
Recently my IDE cable disconnected when the OS was running. After placing back the cable I had the following problems:
- login normally: desktop disappeared (no icons, background image, ..)
- login as root+ running startx manually: the desktop appears, but keyboard and mouse becomes locked forever (nothing happens after ctrl+alt+del or ctrl+alt+F1..)
- error message appears saying update-notifier can't send message to gconfd

I did the following so far:
- rolling back to previous kernel version: no change
- repair boot menu: tried to repair the GUI automatically
- file system check: everything is ok with system partitions (?)
- system update using synaptic
- tried to delete gconfd lock files listed at projects.gnome.org/gconf/ ,but the folders listed there don't exist
- also tried to start sudo gconfd manually, and sudo SIGHUP gconfd 
- deleted /home/user/.Xauthority and similar lock files

According to .Xsession logfile sabayon-apply can't find my user profile,
and update-notifier get timeout error when sending message to gconfd.

With alt+F2  I am able to run apps with GUI. Only the header of the window above menu list is missing. 
 I also have sudo rights, can peform sudo commands with alt+F2+running in terminal, but no idea what to do next. Please, help me. 

System: latest Ubuntu, gnome and xfce desktop installed, autologin to gnome. I can't post logfiles here, because popup windows doesn't appear, and the "paste" right click menu doesn't work. ( I guess the clipboard doesn't running?)

---

### Post by doom3d on 2009-07-12
I managed to disable autologin. Now I can login to xfce, and it works with some errors. Gnome still doesn't work propely. (no icons and menues, but the default background image appears)
Should I reinstall gnome, or what to do next?
I also created a new user. What happens, if I overwrite the original .gconf, .conf or .gconfd folder with the new user's one?

UPDATE: Gnome works propely when logging in as the new user, and still get the original failure, when logging in with original. So wich damaged config file can be the root cause?
Any advice?

UPDATE2: I have deleted home/user/gconf/apps/update-notifier folder, overwritten gconfd/saved-state with the new user's version, and deleted .update-notifier/hooks_seen. Don't know why, but now it works. [http://ubuntuforums.org/images/smilies/smiley-faces-75.gif](http://ubuntuforums.org/images/smilies/smiley-faces-75.gif)

---

