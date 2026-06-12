---
title: "VNC Desktop issues"
date: 2007-09-28
forum: Desktop Environments
---

### Post by bluemike807 on 2007-09-28
Hi there, Im trying to connect, remotely to my Ubuntu machine - using Real VNC for a Windows XP machine - I can connect well enough, but all it displays is the wallpaper/background for my Ubuntu system, and nothing else, save for a mouse cursor - no menus, nothing.

What am I doing wrong? As far as I can tell, all of the settings on both sides are correct... apparently not?

Please help

Thanks

M

---

### Post by lintoon on 2007-09-28
Just a stab in the dark.  Can you change the screen resolution on the vnc client?

---

### Post by lintoon on 2007-09-28
I forgot to mention another option which I use and find it to be very fast.

Check out FreeNX Server for your Ubuntu box.  An NX Client is available for Windows.  It's easy enough to install and setup too.  You only have to change a couple of lines in some config files.

Check out this page for installation instructions:

[https://help.ubuntu.com/community/FreeNX](https://help.ubuntu.com/community/FreeNX)

You don't have to install the NXclient on your Ubuntu system.  The NX client for Windows can be downloaded here:

[http://www.nomachine.com/download.php](http://www.nomachine.com/download.php)

It's certainly worth a try.  You can install both and compare speeds.

A couple of notes:
- Remember to go into your router firewall rules and forward port 8888 to the IP address of your Ubuntu box.
-You probably know this but just in case you don't.  To shutdown your Ubuntu box remotely open a terminal and type "sudo halt"

---

