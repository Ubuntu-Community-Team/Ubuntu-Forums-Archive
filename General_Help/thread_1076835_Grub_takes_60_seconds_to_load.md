---
title: "Grub takes 60 seconds to load"
date: 2009-02-21
forum: General Help
---

### Post by thegamefreak0134 on 2009-02-21
Hi all. I've been searching madly across the net for the answer to my troubles with GRUB on this setup, but no one seems to have a solution that fixes it. That, or its hiding very well.

My PC has two hard drives, a 200G SATA drive, and a 40G IDE drive. I've got my old Vista install on the SATA drive, all by itself, and I installed Ubuntu using mainly default options to the 40G IDE drive. Grub is on the same drive as Ubuntu, so I set that drive up to boot in my bios so that ideally I could choose the OS from there.

I'll note that due to a limitation with the cables I have and my case, I had to install the CD-ROM drive as the master, and the 40G drive as the slave. If this is a known issue, I can rearrange and see if that will solve it.

Anywho, GRUB takes about 20 seconds to say "Loading Stage 1.5", 20 seconds to say "Please wait, Loading GRUB", then 20 seconds again before the menu comes up. I'm sure it's having issues probing one of my drives for something.

Someone said somewhere that the fact that I have no floppy drive might have been the issue, but enabling/disabling that drive in the bios has no effect.

GRUB has no issue seeing and booting both drives, that works just fine. It just takes it forever to get to the menu itself. Is there something I can set in GRUB to fix this, or perhaps a quick rearranging of parts to make it boot easier, or do I need to do something more complex? I do find that because CS3 won't run under Wine that I need to pop into Vista more often than I would normally like, and so this is a pretty major issue for me.

Thanks for any and all help, I'm more than happy to post more info about my filesystems if it will be of assistance.

-Nick

---

### Post by oiad on 2009-02-22
You should never have a cdrom drive and a hdd on the same ide cable.  Can you try booting with just the Hard drive as the master on the ide cable with nothing else hooked up to it?

---

### Post by Hobgoblin on 2009-02-22
> **oiad said:**
> You should never have a cdrom drive and a hdd on the same ide cable.

CDROM and HDD on the same cable isn't so much of an issue but having the HDD as a slave to a read only drive is not advisable.

Can't you just set up the HDD as master and the CDROM as slave (in which case it won't matter which position they are on the cable, even if it is marked master/slave)?

---

### Post by oiad on 2009-02-22
They may have fixed the old problem where the hdd would get slowed down to UDMA33 it is still not advised to put both on the same cable.  Only one device can use the channel at a time, so drive to drive operations that are on the same channel will be much slower than two drives on separate channels.  I usually just invest in the $10-$20 pci ide cards.

---

### Post by thegamefreak0134 on 2009-02-22
I do fully intend to put a second SATA drive in there (the board supports up to 3) which I'm hoping will solve the issue for good. Hang on, I'll switch things around and make the HDD the master, so I'll take the CDROM out completely.

*does this and tests*

Wow. That made all the difference in the world, Grub now loads instantly. Thanks guys! I'll figure out how to put my CD drive in the case in such a way that this will work later. ^_^

So lesson learned: don't put an IDE Hard Drive in Slave Mode that you hope to boot GRUB from, especially when the master on that cable is a Read-Only drive. I'll also note though, I'm not seeing an increase in Ubuntu loading time, so it seems this issue was specific to Grub and Ubuntu itself handled the drive just fine. Weird though.

---

