---
title: "Keyboard issues with intrepid"
date: 2008-12-23
forum: Desktop Environments
---

### Post by am4c130d on 2008-12-23
Hi,

I recently upgraded from Hardy to Intrepid and am now having some keyboard issues.  I use a A4 Tech KL-5UP mini keyboard, which is a USB mini keyboard, it has multimedia buttons, but I don't really use those and a Shuttle SS51G (SIS chipset).

When I first boot in to Intrepid the up/dn/l/r arrows, pgup/pgdn home/end and delete keys don't work.  Xorg keyboard layout is detected as a PC-101 keyboard.  If I change to a console (ctrl alt F1 for example), the keyboard layout works perfectly - i.e. pgup/pgdn scrolls through my history etc..  Switching back to X, the keyboard still has problems.  If I unplug and replug in the keyboard during the X session, the keyboard starts working correctly.  If I logout and log back in, I need to disconnect and reconnect the keyboard again to get it to work properly.  If someone logs in (switch user) while I am logged in, they independently need to disconnect and reconnect the keyboard for it to work for them.

Some comments.

1. This setup has successfully run Ubuntu since Hoary
2. Linux clearly detects the keyboard correctly
3. Xorg doesn't detect the keyboard correctly during login, but does when the keyboard is reconnected during the session

Short of hardcoding the keyboard again in xorg.conf (which I may have tried without success), any ideas as to why I have this problem, and how I can fix it?

Thanks

Alan

---

### Post by EgYPaRaDoX on 2009-01-14
I am using ubuntu intrepid, I have a weird problem, my external keyboard sometimes does work, sometimes doesnt, it always works when i choose the OS to load, any help?

---

### Post by SushiR on 2009-01-15
I have keyboard issues too. No upgrade, fresh install some days ago.
[http://ubuntuforums.org/showthread.php?t=1039852](http://ubuntuforums.org/showthread.php?t=1039852)

---

