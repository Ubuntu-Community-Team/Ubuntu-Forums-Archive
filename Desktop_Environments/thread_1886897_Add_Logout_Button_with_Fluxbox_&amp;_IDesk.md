---
title: "Add Logout Button with Fluxbox &amp; IDesk"
date: 2011-11-25
forum: Desktop Environments
---

### Post by m3bik on 2011-11-25
I have [http://fluxbox.org](http://fluxbox.org) and [http://idesk.sourceforge.net](http://idesk.sourceforge.net) set up on a machine. Everything is working great, but I'd like to be able to set up a Logout icon on the desktop.

I've created the ~/.idesktop folder and created my Logout.lnk file (as instructed) The icon appears on the screen, but when it's clicked, it doesn't logout! Here's the file contents:

> 
table Icon
Caption: Logout
Tooltip.Caption: Logout of Session
Icon: /usr/share/pixmaps/logout.png
Command: logout
Width: 48
Height: 48
X: 59
Y: 209


I've also tried "Command: exit" but it only exits the IDesk application, leaving the user logged in and Fluxbox running!

Also, "gnome-session-save --force-logout" does not work because I'm not using gnome for the session!

What command should be there?

---

### Post by m3bik on 2011-11-25
Well, I found what I was looking for..

According to the tutorial at [http://fluxbox-wiki.org/index.php?title=Howto_exit_fluxbox_with_a_dialog](http://fluxbox-wiki.org/index.php?title=Howto_exit_fluxbox_with_a_dialog) which shows how to exit Fluxbox with a dialog, the command to run is:

kill -TERM $(xprop -root _BLACKBOX_PID | awk '{print $3}')

Which has successfully logged out the user.

---

