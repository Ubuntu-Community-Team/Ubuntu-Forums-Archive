---
title: "Unmounted ISO leaves a .volume file on desktop"
date: 2009-01-26
forum: General Help
---

### Post by bruwstout on 2009-01-26
I have mounted a DVD .iso file by using the archive mounter (right-click) option.  Copied some files off and then right click unmount.  Now when I reboot I have a file on my desktop dvd_name.iso.volume file.  I cannot delete the file.  I can make it go away by re-mounting the iso and unmounting but as soon as I reboot the file is back on the desktop.

Another interesting note is that if I open terminal and ls -l the file isn't listed.


Ubuntu 8.10
Kernel Linux 2.6.27-9-generic
GNOME 2.24.1
Memory: 2 GiB
Processor 0: Intel(R) Core(TM)2 Duo CPU T7250 @ 2.00GHz
Processor 1: Intel(R) Core(TM)2 Duo CPU T7250 @ 2.00GHz

Any help would be greatly appreciated.  Thanks.  :-)

Solution:  I opened the .gkt-bookmarks file located in my home directory.  There was a 'x-nautilus-desktop:///dvd_name.iso.volume' reference entry.  I deleted that entry and the icon was no longer on the Desktop.

---

### Post by bruwstout on 2009-01-29
Any ideas? Anyone?

---

