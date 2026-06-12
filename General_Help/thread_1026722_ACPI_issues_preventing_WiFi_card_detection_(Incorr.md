---
title: "ACPI issues preventing WiFi card detection (Incorrect checksum in table error)"
date: 2008-12-31
forum: General Help
---

### Post by The_PHP_Jedi on 2008-12-31
Hey there,

I'll warn you that this post is detail-heavy, but only so y'all can help me better.

After a hard drive failure (long story), I had to get a new hard drive, and install and reconfigure my Ubuntu install from scratch. My computer is an HP Pavillion a762x, about 6 years old, with a replaced motherboard (same original model, though), so it has quite a few hardware issues w/ Ubuntu (which I had fixed in my previous install gradually as they showed up).

I do have a new issue now that is preventing me from connecting to the Internet, hence I can't really go on setting up the system until I fix it (and I thought setting up NDISwrapper would be the toughest part of this install, heh).

I can't use the onboard Ethernet, since it's not fully functional for some reason (it's an old, used mobo, so...). My WiFi card, a fairly recent Netgear card (can't recall what's the exact model), doesn't seem to be detected by Ubuntu or the mobo properly. I've only had it detected properly once since the new Ubuntu 8.10 install (it worked fine before the new hard drive install, although the computer hadn't been used for months, and I was using 7.10 from a scratch install of 6.10).

After checking dmesg, I found the following error:
```
ACPI Warning (tbutils-0217): Incorrect checksum in table [OEMB] - D5, should be C9 [20080609]
```
That's followed by various ACPI-related errors which affect the WiFi card...

For a closer look, here are the dmesg, lspci -v, and lspci -n outputs:

dmesg: [http://slexy.org/view/s2FCKfgyXW](http://slexy.org/view/s2FCKfgyXW)
lspci -v: [http://slexy.org/view/s2Cfp9Jdcu](http://slexy.org/view/s2Cfp9Jdcu)
lspci -n: [http://slexy.org/view/s2GJslMiqt](http://slexy.org/view/s2GJslMiqt)

I've been told by someone in the Ubuntu IRC channel on Freenode that it might be related to a bug affecting/caused by an onboard Intel integrated graphics card... which this mobo happens to have.

I was Googling most of the afternoon yesterday trying to see if I could get any more details on that bug, or the cause of my problems, to no avail (and I'm a Google Jedi -- I can find anything :P).

So, as a sort-of last resort, I'm posting here to see if anyone has had the same issue, or can offer some insight.

Cheers,
Alesandro

---

### Post by Yellow Pasque on 2008-12-31
Some thoughts:
- Do you have the latest BIOS update for your motherboard? (look on HP's support site)
- Look in the system BIOS for ACPI settings.
- Try playing with the various kernel parameters for ACPI:
```

acpi=off	Don't enable ACPI
acpi=ht	        Use ACPI boot table parsing, but don't enable ACPI interpreter
acpi=strict     Disable out of spec ACPI workarounds.
acpi_sci={edge,level,high,low}  Set up ACPI SCI interrupt.
acpi=noirq	Don't route interrupts
```

---

### Post by The_PHP_Jedi on 2008-12-31
Thanks Temüjin! I'll try those in 2009, since I'll be leaving in a few minutes to celebrate it at a family member's house.

---

### Post by The_PHP_Jedi on 2009-01-02
You'd be amazed at how hard it is to flash a BIOS w/out a local Windows install. I'm still working on it... At least I got the ROM image out of the installer (which took long enough to do!)

---

### Post by The_PHP_Jedi on 2009-01-03
Flashing the BIOS w/ the latest firmware did the trick. I already got the WiFi connection configured and fully working (after some work, though, due to outdated documentation in the Ubuntu Wiki... :-/ )

Cheers!

---

