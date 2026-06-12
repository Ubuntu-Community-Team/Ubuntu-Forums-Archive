---
title: "Kubuntu 24.10 Black lock screen &amp; Plasma(Wayland) not starting Solution"
date: 2024-10-24
forum: Desktop Environments
---

### Post by marktaff on 2024-10-24
I was having some nasty problems with Kubuntu 24.10, which I've solved, and wanted to share in case it helps anyone else.

The machine had an Nvidia card, which I swapped out for an AMD Radeon RX 580 Series as part of the debugging, which didn't appear to make a difference, but it is part of the working system now.

Issues:
1) Plasma (Wayland) wouldn't start.  After entering password, it would go to a black screen, then moments later present the sddm login screen again.
2) In Plasma (X), locking the desktop (manually or after a timeout), would give a black screen with a cursor.  Typing would pass characters to the login field, but you couldn't get any graphics to show up or unlock the desktop. As a work-around, ctrl+alt+f2 followed by ctrl+alt+f1 would make the sddm unlock screen re-appear (which is how I knew characters were getting passed).
3) In System Settings, I could not 'apply' changes to the lock screen.  Any changes remained dirty.

After a day of no progress, I renamed ~/.config to ~/.config.bak, and then rebooted.  This makes KDE rebuild your config from defaults, so you will lose all your settings.  You can undo this by deleting the new ~/.config and renaming ~/.config.bak to ~/.config.  In my case, having KDE rebuild config from defaults fixed all three issues.  I did of course have to spend some time configuring KDE the way I like it.

I recall having to do this with other KDE major upgrades in the past (3->4, 4->5).  We don't get major revisions very often, so no big deal.

Anyway, this worked for me, YMMV, but I hope this helps.

---

