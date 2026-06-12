---
title: "Problems after upgrade"
date: 2006-06-07
forum: Desktop Environments
---

### Post by meimato on 2006-06-07
I recently upgraded from Breezy to Dapper on my ASUS 2800 laptop, and had some problems:
- firefox refuses to start, giving a FLOATING POINT EXCEPTION; I tried deinstalling it, cancelling my .mozilla/firefox folder, but after a new install - at the first boot - it ask me to import settings from another browser, and then crashes again with the same error. Mozilla suite works, as Konqueror does
- I cannot close a session (logoff, reboot, shutdown) regularly; most of the times the system freezes: the screen becomes blank and nothing happens, and i have to push the power button... I don't know it it is an xorg issue: anyway I've got a Mobility Radeon 9600, and use fglrx drivers; during normal works I have no problems with video.

---

### Post by aouie on 2006-06-07
If you are having freezes (or crashes) while shutting down (or logging out / log out / end current session) then disabling spash in the bootup / shutdown sequence should bypass the bug.
As pointed out in [a different post]("http://ubuntuforums.org/showthread.php?t=190769")
disabling splash from /boot/grub/menu.lst will bypass the shutdown freeze.
It worked for me (upgraded to Dapper, NVidia 5950, Athlon 64).
Sincerely,
Aouie

---

### Post by meimato on 2006-06-08
I solved the problem of the logoff crashes: reading though the forums it seems to be an issue related to the fglrx drivers, so I reconfigured xorg to use ati drivers, and now all seem ok.
I still have the problem of the floating point exception by firefox; any suggestions?
Thanks.

---

### Post by scxtt on 2006-06-08
after the de-install (uninstall?) did you remove the firefox folder in /usr/lib? ... i think there's a chance of some residual files that could be left over ... it might also be possible that one of the other browsers, mozilla would be the most likely, is using some resource that firefox needs to start - have you checking in the system manager for any leftover firefox/mozilla procs running?

---

### Post by meimato on 2006-06-08
I installed Mozilla after the problem with firefox, just to have a browser working (I don't like konqueror that much); so the problem doesn't lies in it.
I tried to erase all mozilla/firefox related folders, but I've not checked /usr/lib; I'll give a try.

---

### Post by meimato on 2006-06-09
No way...
It seems it's better if I make a clean install, rather than keeping with my dapper upgraded from breezy.
There are also other minor annoyances, like network configuration freezes... I feal they were not as ready as usual, but have pushed the release to keep in touch with the already delayed schedule.

---

### Post by scxtt on 2006-06-09
honestly, i didn't have much luck (or liking for the results) upgrading from breezy to dapper ... but a fresh install of dapper suits me just fine :)

---

