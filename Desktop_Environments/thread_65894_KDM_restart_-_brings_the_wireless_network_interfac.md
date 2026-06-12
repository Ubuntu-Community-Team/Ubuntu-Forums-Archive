---
title: "KDM restart - brings the wireless network interface down!"
date: 2005-09-15
forum: Desktop Environments
---

### Post by daller on 2005-09-15
Hi All,

I have a HP Pavilion (laptop), and everytime i restart KDM (Ctrl+Alt+Backspace), it brings my wireless network interface down!

This also happens when I close the lid, or leave the laptop idle (after a display-shutdown)

---

### Post by mlomker on 2005-09-15
That's odd.  I don't recommend using ACPI features...they aren't even all that consistent on Windows.  My Mac was the only machine that has ever been reliable with that.

---

### Post by daller on 2005-09-16
Which ACPI-features do you mean?

---

### Post by mlomker on 2005-09-17
[QUOTE=daller]Which ACPI-features do you mean?[/QUOTE]

Hibernating and suspend.  You're right that I should have clarified--ACPI has a lot of other useful pieces to it, like CPU throttling.

---

### Post by daller on 2005-09-20
I did not activate Hibernating or suspend (Closing the lid simply turns the screen off... I think - never saw the display when the lid is closed, actually :))

These are the problems that clearly brings my network interface down:

- Restarting KDM - This shouldn't mean anything to the wireless setup, should it?
- Closing the lid, does this activate any ACPI-function, if not specified?
- Leaving the pc idle, until display shutdown - Another ACPI-trigger?

---

### Post by winxp2kubuntu on 2005-09-20
I have the same problem with my wireless adaptor (NetgearMA401).
After several hours editing all sorts of files, a couple of reinstalls and a bit of diging on the net, it appears it's a bug in the Kubuntu boot sequence when the network services are initialized. From what I can gather, the bug hasn't been fixed yet. Something to do with DHCP client. In the mean time, you can fix your problem by opening a Konsole and typing :
sudo dhclient eth0 
or
sudo dhclient eth1

depending on which adaptor you want to enable. This solves my problem so far.
Hope it works for you.
Couple of links where the problem is discussed:
[http://bugzilla.ubuntu.com/show_bug.cgi?id=290](http://bugzilla.ubuntu.com/show_bug.cgi?id=290)
[http://bugzilla.ubuntu.com/show_bug.cgi?id=13497](http://bugzilla.ubuntu.com/show_bug.cgi?id=13497)
Cheers.

---

### Post by mlomker on 2005-09-20
My best guess would be that your laptop powers down the wireless adapter during ACPI events.  Have you explored the options in your BIOS to see if there are any adjustments related to the adapter and power management?  If there is an option to leave it on then that'd be a good thing to try...

---

