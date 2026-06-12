---
title: "Kubuntu Live CD - Wont Boot on 3 machines i've tried. MD5 Checks out ok! Help Please."
date: 2005-08-24
forum: Desktop Environments
---

### Post by mightymidget on 2005-08-24
Hi All,

Anybody got a solution to this? My MD5 checks out ok but Kubuntu Live refuses to boot on all 3 of my machines!

It get to the stage where it says 'checking battery state' and just keeps respawning or something like that.

I've read elsewhere in this forum people are having the same problem, but so far no one seems to have a definative answer.

This is the latest live version 5.04-5

Please can someone help, or is this version of Kubuntu Live just no good?

Many thanks in advance

Andy

---

### Post by cwaldbieser on 2005-08-24
[QUOTE=mightymidget]Hi All,

Anybody got a solution to this? My MD5 checks out ok but Kubuntu Live refuses to boot on all 3 of my machines!

It get to the stage where it says 'checking battery state' and just keeps respawning or something like that.

I've read elsewhere in this forum people are having the same problem, but so far no one seems to have a definative answer.

This is the latest live version 5.04-5

Please can someone help, or is this version of Kubuntu Live just no good?

Many thanks in advance

Andy[/QUOTE]
Well, it is hard to definitively diagnose that kind of problem.  I have had situations where the Ubuntu live CD will not boot in a particular PC, but Knoppix will, and sometimes the other way around!  If the Live CD doesn't seem to boot anywhere, sometimes that can mean that the CD wasn't burned correctly, or maybe the media is just substandard, etc.

One mistake that beginners sometimes make is they *copy* the .iso file to the CD instead of creating a bootable image from the .iso.  Since there are lots of different programs for burning software, it is probably best if you tell us what program you used, and then someone who is familiar with that program can ask you questions and determine if you followed the correct procedure.

---

### Post by t2kburl on 2005-08-25
I have the same problem and I know I burned it properly

---

### Post by incinerator on 2005-08-25
iirc, once the livecd gets to that state you mentioned it has already tried to start kde. You should see a related message a couple of lines above the "checking battery state" message. However, for some reason starting kde fails. A likely reason is the X-server that fails to start, probably because it doesn't deal with you gfx card properly. This particularly happens on laptops equipped with GeforeGo graphics chips.

I would check out the help menus you can access in the boot loader pressing one of the "Fx" keys. Then try some of the kernel boot options listed on these help pages, particularly the "vga=771" option. Other options of interest may be the "noapic nolapic", "acpi=off" and "pci=noacpi" options.

If everything fails, cross-check with a normal Ubuntu live-cd. Then file bug reports appropriately, not forgetting to mention the exact h/w configuration of your system.

---

