---
title: "Cannot mount external usb hard drive"
date: 2008-12-27
forum: General Help
---

### Post by blooddrunk on 2008-12-27
Hi! I recently upgraded my Ubuntu from 8.04 to 8.10. I just bought myself an external hard drive. The problem is that the first time i plugged it in and turned it on, I got the following error: Unable to mount the volume. $logFile indicates unclean shutdown(0,1). Failed to mount '/dev/sdb11': Operation not supported Mount is denied because NTFS is marked to be in use

What should I do?

---

### Post by nucleuskore on 2008-12-27
Connect it to a Windows machine

Note the drive letter. If the drive letter is X:

Then open a terminal and type 

chkdsk X: /F /V

This will repair the filesystem. Then right click on the icon in the system tray and safely remove the drive. If this does not work shut down the system and remove the drive.

---

### Post by HereInOz on 2008-12-27
You may get away with just re-connecting it to a Windows machine, and then properly disconnecting it, with the icon in the system tray, rather than just pulling the plug. Then try it in your Ubuntu machine. 

There may not be anything wrong with the file system at all, so try this first.

---

### Post by blooddrunk on 2008-12-27
It didn't work. The drive mounts perfectly in Windows, but still gives me the same error in Ubuntu 8.10

---

### Post by Bucky Ball on 2008-12-27
That is after closing it in windoze, switching off then shutting down windoze?

---

### Post by vanadium on 2008-12-27
You did not properly check nor properly disconnect it in Windows, likely. If the ntfs file system is clean, ubuntu will mount it. Eventually boot into Windows and shut down Windows twice before trying to connect it in Ubuntu.

---

