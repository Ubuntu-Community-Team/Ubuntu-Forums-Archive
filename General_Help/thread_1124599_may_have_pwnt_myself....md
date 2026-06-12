---
title: "may have pwnt myself..."
date: 2009-04-13
forum: General Help
---

### Post by Gizenshya on 2009-04-13
ok, was going to try out backtrack3 by nstalling it to a usb flash drive.  everything went good until I ran the bootinst.dat file.  I got an access denied error, so I right-clicked and ran it FROM THE DRIVE as admin.  well, for some reason it ran it FROM THE C DRIVE and may have completely screwed my mbr.

atm I am dual-booting Vista and Ubuntu (installed from within vista).

I want to make sure everything is in order before attempting to reset, as I might not be able to get back.  last time this happened (no, not from something I did :p ) I wasn't able to repair it after restart, and I had to reformat and whatnot.

So... how do I check the status of my mbr?  how do I check if my boot loader will do what it normally does?

ohh, and while I'm at it, I'd like to change the default boot OS to ubuntu.

---

### Post by soltanis on 2009-04-13
Don't worry; even if your system doesn't boot, you can use a LiveCD to access it (so um, you might want to be sure you burn one of those).

EDIT.

Don't do what I said below; reinstalling GRUB is a better idea.
If your computer fails to boot, insert the LiveCD. After booting is finished, open an terminal and do
```

sudo grub

(in grub)

root (hd0,0)
setup (hd0)
quit

```

Replace (hd0,0) with the partition where your Linux installation is located (/dev/sda = 1st hard disk, 1st partition = (hd0,0), /dev/sda1 = 1st hard disk, 2nd partition = (hd0,1) and so on).

One more thing, however you configured GRUB to boot windows, you will also have to reconfigure it in the GRUB session so that both your operating systems will boot.

===========================================================================================================================

Vista can probably solve this problem better than Linux can. Reboot your computer, check to see if it's still alive. If not, insert the Vista DVD, reboot, then go to "Repair your computer" on the installation screen and hit Windows Vista -- Command Prompt.

At the prompt execute

```

bootrec.exe /fixmbr
bootrec.exe /fixboot

```

That will remove GRUB so you will have to reinstall that (your computer will boot to Vista only, as is the Microsoft way).

---

### Post by Gizenshya on 2009-04-13
ok, wish me luck :(

---

### Post by Gizenshya on 2009-04-16
Hmmm... I restarted and it's fine.  no issues at all.

This is bittersweet, though.  I'm trying to install BackTrack3 onto a USB drive and it's justnot working.  That file doesn't seem to activate the drive to boot correctly.  Since it didn't even screw up this one like it was suppossed to, I don't know what to make of it :(

but thats another issue I guess.. and probably one for backtrack forums.  (unless someone here knows and would like to shoot me a message :) ).

---

