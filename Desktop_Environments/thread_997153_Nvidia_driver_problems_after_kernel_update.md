---
title: "Nvidia driver problems after kernel update"
date: 2008-11-29
forum: Desktop Environments
---

### Post by Cammy on 2008-11-29
I'm running ubuntu Hardy and an NVidia 6200LE video card.  I recently installed the Nvidia beta driver (180.06) to fix a problem with desktop effects, and everything's been fine since.

This morning, I had an update notification, so I let it run.  It updated my kernel from 2.6.24-21-server to 2.6.24.22-generic.  This of course required a reboot.  After the reboot, it came up in that screen with the "Please configure your display" dialog box, and that huge "X" shaped cursor.

After fiddling with it all morning, I can only get the machine to boot up properly by following this procedure:

1) Boot up into the latest kernel, recovery mode.

2) Go in as root and get a command prompt (3rd option I think)

3) Find the current video driver, and reinstall it using 'sh driver-name'

4) After the install, type "exit" then pick "resume normal boot.

That gets you in with a proper driver. Anything else gets to that darn display screen.

Any help fixing this would be GREATLY appreciated.

---

### Post by m_l17 on 2008-11-30
Take a look at this:

[http://ubuntuforums.org/showthread.php?t=835573]("http://ubuntuforums.org/showthread.php?t=835573")

---

### Post by Cammy on 2008-11-30
Hey thanks!  That's perfect.

---

