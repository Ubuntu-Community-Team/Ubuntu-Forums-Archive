---
title: "Cannot boot..."
date: 2006-06-01
forum: Desktop Environments
---

### Post by Core407 on 2006-06-01
I installed the fxgl (sp?) driver for ATi 8500 cards in Ubuntu and when I try to restart, everything checks up on boot, but the screen stays black after and just hangs. Any ideas? Right now I'm off the live CD so I can still mess around with it.

---

### Post by Neobuntu on 2006-06-01
[QUOTE=Core407]I installed the fxgl (sp?) driver for ATi 8500 cards in Ubuntu and when I try to restart, everything checks up on boot, but the screen stays black after and just hangs. Any ideas? Right now I'm off the live CD so I can still mess around with it.[/QUOTE]

Well try this. (It will back up your old file)

...after loging in: (cut and paste this for ease) ..but wait you're on another computer or boot aren't you? Jot it down and note that hitting the <TAB> key will fill in some works for you speeding things up (when you have to manualy type) and reducing typos.

sudo dpkg-reconfigure xserver-xorg

...and hold down enter to select all the defaults.

This is a quick way to turn off the fxgl driver so you can get back at it.

Then restart OR "sudo /etc/init.d/gdm restart" (using gdm, kdm, wdm; whatever) in there OR just type "startx" for testing.

Also note: what I like to do (if online) is:

sudo apt-get install mc

For the old Midnight Commander so I have a quick way to edit directories and files when WITHOUT a GUI. Type "mc". You can edit your config files with it.

---

