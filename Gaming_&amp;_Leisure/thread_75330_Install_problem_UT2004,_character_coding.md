---
title: "Install problem UT2004, character coding"
date: 2005-10-13
forum: Gaming &amp; Leisure
---

### Post by Snewton on 2005-10-13
Try to run, run in terminal or open the linux-installer.sh file on the first install cd of UT2004, but nothings runs, and Gedit tells me this:

"gedit was not able to automatically detect the character coding. Please, check that you are not trying to open a binary file and try again selecting a character coding in the 'Open File...' (or 'Open Location') dialog."

I've tried with UTF-8 and ISO-8859-15, but does'nt work. I can add other character codes, but there so many...

Anyone knows what to do?

---

### Post by Snewton on 2005-10-13
Uups, I'll search next time, [http://ubuntuforums.org/showthread.php?t=33396&highlight=install+ut2004]("http://ubuntuforums.org/showthread.php?t=33396&highlight=install+ut2004")

EDIT: This article solved my problems with switching disks:

[http://www.linux-gamers.net/modules/wfsection/article.php?articleid=18](http://www.linux-gamers.net/modules/wfsection/article.php?articleid=18)

I turned off automount in the *System-Preferences-Removable drives and media*

The trick is to NOT start the shell script when you are in the cdrom dir, but from the media dir with # ./cdrom/linux_installer.sh
If you are in the cdrom dir and use # ./linux_installer.sh you will not be able to unmount the disks.

To mount the other disks open a second terminal window, go to the media dir (cd /media) and type *mount cdrom* whenever you insert a new disk.  :)

---

### Post by xeta on 2005-10-13
was just about to paste that url in.

---

