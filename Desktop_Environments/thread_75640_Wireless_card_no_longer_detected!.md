---
title: "Wireless card no longer detected!"
date: 2005-10-14
forum: Desktop Environments
---

### Post by EnderTheThird on 2005-10-14
I did a fresh install of Breezy last night, and was surprised that my wireless card (D-Link AirPlus DWL-G520 Wireless PCI Adapter (Rev. B)) worked with no problems.  It hadn't been working with the previous Breezy versions, at least not while I had WEP enabled with my router.  So last night I set my computer to hibernate when I went to bed, and when I woke up this morning the computer was off.  I'm not sure if that's relevent, but I thought I should mention it.

Anyway, when I booted up after I got home tonight, it no longer showed my wireless card under the Networking Settings.  I looked through Device Manager, but didn't see a way to tell Ubuntu to scan my computer for any new hardware or to add a new device.

Any ideas?  It's a real pain having to move my router around so I can get my network cable to reach if I want to use the Internet while I'm in Ubuntu.  Oh, and the card still works in XP, so I know it's not a sudden hardware problem from the hibernation/power off thing I mentioned earlier.

---

### Post by Dr. Nick on 2005-10-14
Do you know what kernel module you were using, may need to load it by hand a first using modprobe. Have a look at the kernel logs using ```
dmesg
``` and see if you notice anything. When I resume hibernation I have to reload my wireless module for it to show up in netwwork manager ,so hopefully your solution would be just as easy

---

### Post by EnderTheThird on 2005-10-14
My output from dmesg is too large to insert as a message or attachement, and I'm not really sure what I'm looking for to begin with.  All I really saw was a bunch of entries about unknown keys being pressed and then released.  I'm still pretty new to Ubuntu and Linux in general, but I have no problem following any suggestions you guys might have.  I *could* always reinstall and not try to put it in hibernate again, but I'd rather try to fix it first.  Thanks!

---

### Post by Dr. Nick on 2005-10-14
look in dmesg for anything related to net: or wlan0 or something saying module unloaded. Most likely toward the bottom. Will a restart fix it or does it still not show up?

also type ifconfig in a terminal and see what shows up, if you have a wired lan also you should get 3 entries "lo" "eth0" and either "eth1" or "wlan0"

---

