---
title: "[SOLVED] Documents desktop shortcut checkbox disabled"
date: 2014-09-06
forum: Desktop Environments
---

### Post by fredbird67 on 2014-09-06
This happened on a fresh Ubuntu 14.04 mini-CD installation with LXDE added from the command line after installation.  For some reason I cannot figure out, whenever I go to the "Desktop Preferences" dialog box, everything works fine except for the Documents desktop shortcut option checkbox being disabled, as shown in the following screenshot:

[IMG]https://copy.com/66SyFSB4iji4[/IMG]

Does anyone have any idea what could be causing this?

Thanx in advance,
Fred in St. Louis

---

### Post by fredbird67 on 2014-09-07
I figured it out on my own.  I was also having a problem of there not being the different folder icons for Desktop, Documents, Music, Pictures, Videos, and the like, and I learned that I needed a user-dirs.dirs file in my ~/.config directory.  But then, I got to wondering if there was by any chance a package that took care of all of that, so I did a search of Synaptic, and sure enough, there was, so I downloaded and installed xdg-user-dirs along with xdg-user-dirs-gtk, closed everything, rebooted, and there I had all the custom home directory icons.

Honestly, I wasn't really expecting that to do anything for me with the other problem...but when I went into the desktop preferences, I found that I was now able to select and deselect the documents folder shortcut for the desktop.  Don't quite know what's up with that, but all I know is I'm happy to have solved the problem, even if it was by first fixing something else that was a minor annoyance.

---

