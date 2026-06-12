---
title: "Grub error 24,16 on updated kernels"
date: 2009-05-26
forum: General Help
---

### Post by iamretr0 on 2009-05-26
Hello.  I recently moved some equipment around to simplify my network.  I have an install of mythbuntu 8.10 working as a backend and wanted to use it as frontend/backend.  To that end, I installed all the updates, and that downloaded a newer kernel.  When I tried to boot, it came up with grub error 16, and all I got was a grub command line.

I worked around that by unhiding the menu and giving myself some time to select another kernel, which allows me to use older kernels fine, but not the newest one nor it's recovery mode.  

Against my better judgement I updated to 9.04, which I use and love on a notebook.  It's kernel also doesn't work, and it gives the error code 24 in grub.  Again, I can still use older kernels.

What should I be looking at as the culprit for these two errors, and is there a solution?

---

### Post by iamretr0 on 2009-05-28
Any thoughts on how I can correct these error conditions?

---

### Post by VMC on 2009-05-28
Below is a breif note on the errors. Can you print out the old and new changes to menu.lst file.


> 16 : "Device string unrecognizable"
This error is returned if a device string was expected, and the string encountered didn't fit the syntax/rules listed in the Filesystem Description.
24 : "Cannot boot without kernel loaded"

This error is returned if GRUB is told to execute the boot sequence without having a kernel to start.

Here's some more on that file system error [#16]("http://www.uruk.org/orig-grub/filesystem.txt")

---

### Post by kulturloseramerikaner on 2009-05-29
Anyone that is multibooting should have one of these:
[http://www.supergrubdisk.org/index.php?pid=5](http://www.supergrubdisk.org/index.php?pid=5).
This is essentially GRUB on a live CD and has saved my rear many times.  It gives you the ability to reinstall, restore, etc, GRUB after issues happen.  What it sounds like is happening is that GRUB is looking for the UUID of Myth and not finding it.  Try a reinstall from the SuperGRUB disk, it should catch all drives and partitions as if it was being installed to the system for the first time.

---

