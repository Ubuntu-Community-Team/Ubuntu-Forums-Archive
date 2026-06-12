---
title: "xubuntu 9.10 installation quit unexpectedly"
date: 2009-10-30
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Jon_J on 2009-10-30
I was installing xubuntu 9.10 from a cdrom "xubuntu-9.10-desktop-i386.iso"
When it got to "setting up locals", I pressed "Skip" because I didn't need all the language files.
I have done this before on other installations such as xubuntu 9.04 and debian 503.
The installer just quit and asked if I wanted to report the problem.
I didn't have an internet connection, so I just closed this dialog.
I did a quick check and it looked like the directory structure was there, but I'm not sure.
I'm installing this on a Mini-10 with 3 other OS's booting via grub legacy.
One other thing I did while in the "partitioner" setup, is clicked "Advanced" and unchecked "Install Boot Loader"
I was hoping to just edit my /boot/grub/menu.lst under Debian and add this installation later.
I tried using the installer shortcut on the desktop of the Live CD again, 
but it looked like it was going to install from the beginning, not from where I left off.
I'm using an old Creative 32x read cd drive and it takes a long time to install this version.
If there is no solution to this, I'll probably just boot into my 9.04 installation and format that partition and start over.

---

### Post by mikewhatever on 2009-10-30
If the computer has no internet connection, you don't need to hit the Skip button. The installer will try downloading and skip automatically. Grub needs to be installed, not to hd0, but to the system partition, thogh I am not quite sure how to boot that later.

---

