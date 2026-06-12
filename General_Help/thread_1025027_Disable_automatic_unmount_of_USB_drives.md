---
title: "Disable automatic unmount of USB drives"
date: 2008-12-29
forum: General Help
---

### Post by retrovertigo on 2008-12-29
I have several documents that I routinely need to access from my work computer (running Ubuntu 8.10) and my MacBook Pro at home.  I am using a USB flash drive to carry the files with me and work on them at both locations.  However, recently the USB stick is unmounted after a period of inactivity.  This is particularly annoying when I'm editing some documentation in OpenOffice.org Writer and I'm called away from my workstation for a while, then go back to make some changes and save the document, only to be told that the file does not exist.

Like I said, this is a fairly recent phenomenon.  This never happened with Hardy (at least, not that I remember), so it may be related to an issue with Intrepid, or a new feature designed for better power management.  Thinking it might be a power-saving feature, I checked the Power Management menu under System->Preferences, but didn't see anything about automatically unmounting drives.

---

### Post by Agent ME on 2008-12-29
I've also been annoyed at this too, and have seen this happen in older versions of Ubuntu too.

Not really a solution, but to remount the flash drive after its been auto-unmounted, you just have to click Places -> [flash drive name]. You don't need to unplug it and plug it back in if you've been doing that.

---

### Post by retrovertigo on 2008-12-29
That's just the thing though... it disappears from the "Places" menu, as well as from Nautilus.  I've looked at /var/log/syslog and /var/log/messages to see if there are any errors that might be causing the drive to unmount, but I haven't seen anything.

---

### Post by dcstar on 2008-12-29
> **retrovertigo said:**
> I have several documents that I routinely need to access from my work computer (running Ubuntu 8.10) and my MacBook Pro at home.  I am using a USB flash drive to carry the files with me and work on them at both locations.  However, recently the USB stick is unmounted after a period of inactivity.
.......
Like I said, this is a fairly recent phenomenon.  This never happened with Hardy (at least, not that I remember), so it may be related to an issue with Intrepid, or a new feature designed for better power management.  Thinking it might be a power-saving feature, I checked the Power Management menu under System->Preferences, but didn't see anything about automatically unmounting drives.

I have USB drives in 8.04 that never unmount in the way you describe, so if I were you I'd report this as a bug.

---

### Post by mostafa.bazzaz on 2009-01-16
I have same problem with my 8GB transcen and 1GB kingstone.

Intrepid 64 bit (default kernel)
Intel E7300
2x2GB DD2-800

---

