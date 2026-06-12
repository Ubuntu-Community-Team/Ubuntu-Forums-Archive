---
title: "Single and Double Click are sending extra 'click' in Gnome"
date: 2009-12-03
forum: Desktop Environments
---

### Post by samalex on 2009-12-03
Hi,

I'm running Ubuntu 9.04 Desktop, and I've noticed some weirdness where sometimes when I single click it sends a double-click, and likewise when I double-click it sends three clicks.  But it doesn't always do this...  

I started really noticing it after installing the gok package through Synaptic because I wanted to use the on screen keyboard, but even after uninstalling the package the problem persisted.

A few things like clicking menus and having them open then close plus single clicking on an email in Thunderbird with it opening in a new window were the first signs.  Then I went into Thunderbird properties where it has the notification sound, and clicking Preview once causes the sound to chime twice... and double clicking Preview the chime plays three times.  But if I wait a bit and single click it will play once, only when I singe click a couple of times in so many seconds does it start sending two clicks with one press of the mouse button.

Any suggestions???  I've reinstalled gok to see if I could find some setting that may have been switched inadvertently, but thus far I haven't seen anything.  I'm about to log in as another user account to see if this persists, but are there any settings in Gnome I can check at the file level that may show what's happening, whether through Gnome or the Accessibility stuff installed through the gok package?

Thanks for any advise, this is driving me nuts!

Sam

---

### Post by samalex on 2009-12-04
I've found a solution that works...  I had removed the gok package after this problem started, but that didn't help.  I reinstalled then to see if I could further tweak the gok settings but no luck.

I think after uninstalling the gok package I needed to reboot, which I didn't do.  After removing gok I rebooted and after Gnome came up it asked about sticky keys and whether I wanted to enable or disable them.  I chose disable and all seems to be working fine now.  

Crazy...  I don't know if it was sticky keys or gok causing the problem, but it seems to be gone now.  The only thing left is the Accessibility icon (looks like mens room sign) in the taskbar, but if it bugs me too much I'm sure I can find how to remove it with some digging :)

Thanks...

Sam

---

### Post by samalex on 2010-03-25
Actually here we are 4 months later and it's still happening, just intermittently.  Anyone ever see this?

---

