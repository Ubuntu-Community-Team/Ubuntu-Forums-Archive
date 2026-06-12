---
title: "Cannot get into default or failsafe Gnome session, only failsafe term"
date: 2006-08-26
forum: Desktop Environments
---

### Post by mrkipling on 2006-08-26
Hello everyone,

I'm having a major problem with my Ubuntu installation at the moment. Usually I'm able to fix it by reading other people's threads, but this particular problem has had me frustrated for hours with no solution!

Basically, whenever I log in to Ubuntu (using Gnome or failsafe Gnome as the session) I get the message about $HOME/.dmrc being ignored and permissions needing to be set to 644. I've tried the various fixes for this problem to no avail. I then go to an empty screen with a coloured background and the mouse pointer, but nothing else. At this point I am forced to hit CTRL-ALT-BACKSPACE to get back to the login screen.

I can, however, get into the failsafe terminal. I still get the $HOME/.dmrc message, but after this I am able to access the terminal. From here I can type 'metacity &' and 'gnome-panel' which gives me a fairly functional Ubuntu desktop, with access to all of my applications (such as Opera, which I am using at the moment to write this) and system settings menus.

However, I would very much like my default Gnome session restored to it's former glory! I've tried the following:

[LIST]
[*]sudo apt-get install xserver-xorg --reinstall
[*]sudo apt-get install gdm --reinstall
[*]sudo dpkg-reconfigure xserver-org
[*]sudo dpkg-reconfigure gdm
[/LIST]

...but they haven't had any effect. I've replaced xorg.conf and gdm.conf with backups, and this hasn't helped either. I'm running 6.06 AMD64.

Any help would be greatly appreciated.

---

### Post by Endolith on 2007-12-14
Try renaming ~/.gnome2/session to something else

---

