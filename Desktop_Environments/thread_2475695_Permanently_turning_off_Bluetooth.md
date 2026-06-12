---
title: "Permanently turning off Bluetooth"
date: 2022-06-04
forum: Desktop Environments
---

### Post by thumper76 on 2022-06-04
I'm running Ubuntu 20.04 LTS. If I click off Bluetooth in the Settings panel, it doesn't stay off on a reboot. How can I set it permanently to off ?

---

### Post by ajgreeny on 2022-06-04
Use command
**sudo systemctl disable bluetooth**
That should do exactly what it says, ie, disable Bluetooth completely even after a reboot.

Should you ever want it back running again use command
**sudo systemctl enable bluetooth**
and then to actually run it use command
**sudo systemctl start bluetooth**

---

### Post by TheFu on 2022-06-04
You can also blacklist the bt kernel module or disable it in the BIOS of the computer.  I do both of those on my laptop after being hacked through bluetooth at a tech conference a few years ago.

I would add that masking the service would be another step to disabling it.
```
sudo systemctl mask bluetooth
```

---

### Post by ActionParsnip on 2022-06-06
Turn it off in BIOS if you never intend to use it (If possible)

---

### Post by #&amp;thj^% on 2022-06-06
> **TheFu said:**
>   I do both of those on my laptop after being hacked through bluetooth at a tech conference a few years ago.

Ok this makes more sense to me now, when you first reported it back then... I don't recall you mentioning that Important fact.

---

### Post by TheFu on 2022-06-06
> **1fallen said:**
> Ok this makes more sense to me now, when you first reported it back then... I don't recall you mentioning that Important fact.

Bluetooth is hackable.  That's the only important fact.  Don't use it, unless you are willing to be hacked.  BT may seem to be a minimal risk, because they claim it only works 10m, maximum, but people have connected from over a mile away.  So ... the people who shouldn't be worried about BT are those that live farther than 1 mile from their closest neighbors AND a road that could have traffic looking for BT/wifi APs.

BT headsets, keyboards, speakers are really fun to screw around with ... especially if they aren't yours.  I find it shocking that anyone would use BT for their keyboard or mouse.  Just hand over your computer to someone else already.

Car locks that are based on BT have been cracked too. There are relay attacks used while the owner is off shopping. Their car is stolen.  There have been fixes for the different vehicle attacks, and each time a new attack that gets around it is working in a few months.

Don't trust bluetooth.  That's the headline.

When I was hacked. I'd performed a fresh install the day before. Complete wipe.  Fulling patched. Very few extra programs added.  It the time, I was in a hurry to catch a flight, so I didn't have time to go through my normal security checks.  Ubuntu enabled BT by default, even though I wasn't using it and have never used it more than just for hacking research.

Don't trust bluetooth.  That's the headline.  The version doesn't matter.  The BT standards committee is more about usability and the appearance of security, not real security.  They are the TSA of computing.

---

