---
title: "[SOLVED] Suspend Without Restarting X?"
date: 2008-08-17
forum: Debian
---

### Post by mthei on 2008-08-17
Hi.
I've recently switched from Fedora to Debian, where Suspend works with both. However, with Fedora, I was able to Suspend and resuming would take me back to my desktop, but whenever I would ctrl-alt-backspace to restart X, my resolution, which is normally supposed to be 1440x900, would stretch out to 1024x700, but it would be fine if I just stayed on my desktop. I only mention this because with Debian Lenny, when I resume, it takes me back to the login screen, and therefore am given the stretched out resolution, and the only option is to reboot.
Is there anything I can do so that when I resume, I'm back at my desktop with the same resolution? My video card is well supported, as the problem seems to lie with the actual monitor (Acer AL1916), as the latest OpenSUSE has also given me trouble related to the monitor.

---

### Post by p_quarles on 2008-08-17
I would suggest running the "pm-suspend" script with the various different "quirks mode" arguments listed in the man page. You may find that your display relies on a quirk that is causing the unwanted behavior, and the suspend command may be able to compensate for that quirk if it knows it's there.

---

### Post by mthei on 2008-08-17
Thank you for your reply, but that was one of the first things I've tried after my initial search, and when I tried what I thought would work, trying to suspend just sent me back to the login screen.

---

### Post by mthei on 2008-08-23
Well, I found a [temporary fix](http://forums.debian.net/viewtopic.php?t=28388&highlight=suspend) by searching the Debian forums which I had seen before but ignored because it's not really the same problem. The advice in the second post fixed my issue as well, but the file has to be re-edited every time pm-utils gets updated.

My Debian install is now running as well as Fedora was for me, and remarkably lighter, too.

---

