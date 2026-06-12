---
title: "KDE 3.5.5 doesn't automount my USB key"
date: 2006-12-26
forum: Desktop Environments
---

### Post by MacMan on 2006-12-26
Ciao,
I've been looking for a solution to this problem in this forum and in Launchpad for a while but didn't find any yet.

Kubuntu Dapper, KDE 3.5.5. My USB key/mp3 player doesn't get automounted when I plug it in. Konqueror shows the USB key icon but when I click on it an error message pops up saying "**An unknown error occured**".

KDE correctly detects the device node (/dev/sdb1) and the file system used (VFAT32).

Typing this in a command line works:
```

pmount /dev/sdb1

```
When I type this command (as a regular user, no sudo) the key gets mounted and I can read and write it with no problem at all.

Some additional info to show that I did my homework :-)
```

$ id hal
uid=111(hal) gid=111(hal) gruppi=111(hal),24(cdrom),25(floppy),46(plugdev)
$ groups
macman adm dialout cdrom floppy audio dip video plugdev lpadmin scanner admin haldaemon players wineuser
$ grep sdb /etc/fstab
$

```

hal, dbus and pmount are installed. I believe the automounting feature stopped working after I updated KDE to 3.5.5 . My CDs and DVDs **do** get automounted all right.

Any suggestions?

Thank you a lot for any help, and happy holidays to everybody! :-)

Ciao.

---

### Post by MacMan on 2007-01-03
No ideas at all?

Ciao.

---

### Post by hoheszeh on 2007-02-18
I ve got exactly the same problem. Did you find a solution?

---

