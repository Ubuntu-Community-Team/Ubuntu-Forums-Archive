---
title: "Please respond! Failed to Initialize HAL"
date: 2009-03-13
forum: General Help
---

### Post by Liesmith Loki on 2009-03-13
Hey guys. Ubuntu has been working fine for me for a while, but then a couple of days ago, out of the blue, an error pops up at startup and says "Failed to Initialize HAL", and there's no internet connection.

This was soon followed by a need to run a manual FSCK since there were some disk inconsistencies which auto disc check couldn't fix, which I did, so now at the very least, it boots up to the desktop now, but the Failed to Initialize HAL still appears, and still not network connection.

My network is connected directly to my computer through ethernet cable.

I've tried to restart HAL, but it says:

rm: cannot remove `/usr/share/hal/fdi/policy/gparted-disable-automount.fdi': Not a directory.

Can I get any help on this? And I don't have a net connection like I said before, so I can't use apt-get to reinstall it.

Can't someone help me out, seriously? >=[

When I try to reinstall via Synaptic, it attempts to download something through the internet which I can't do since it's disabled, and I get the error

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu5_i386.deb)
Could not resolve 'us.archive.ubuntu.com'.

I've tried the trick where you put in a CD before boot up, and that doesn't work. I've tried reinstalling HAL through Ubuntu Live CD but I still get the same errors, even though when I'm running through Ubuntu LiveCD, I can access the internet.

PLEASE RESPOND.

---

### Post by dcstar on 2009-03-14
> **Liesmith Loki said:**
> Hey guys. Ubuntu has been working fine for me for a while, but then a couple of days ago, out of the blue, an error pops up at startup and says "Failed to Initialize HAL", and there's no internet connection.

**This was soon followed by a need to run a manual FSCK since there were some disk inconsistencies which auto disc check couldn't fix**, which I did, so now at the very least, it boots up to the desktop now, but the Failed to Initialize HAL still appears, and still not network connection.

My network is connected directly to my computer through ethernet cable.

I've tried to restart HAL, but it says:

rm: cannot remove `/usr/share/hal/fdi/policy/gparted-disable-automount.fdi': Not a directory.

Can I get any help on this? And I don't have a net connection like I said before, so I can't use apt-get to reinstall it.

Can't someone help me out, seriously? >=[

When I try to reinstall via Synaptic, it attempts to download something through the internet which I can't do since it's disabled, and I get the error

W: Failed to fetch [http://us.archive.ubuntu.com/ubuntu/...untu5_i386.deb](http://us.archive.ubuntu.com/ubuntu/...untu5_i386.deb)
Could not resolve 'us.archive.ubuntu.com'.

I've tried the trick where you put in a CD before boot up, and that doesn't work. **I've tried reinstalling HAL through Ubuntu Live CD but I still get the same errors**, even though when I'm running through Ubuntu LiveCD, I can access the internet.

PLEASE RESPOND.

The system obviously has major problems now, you should back up your /home folder to an external device as I would say a reinstall may be the quickest way of resolving things. You can then restore all of your data in your saved /home folder.

If you are also getting errors with the Live CD then you should check your hardware, there may be a problem that is not related to the software.

---

