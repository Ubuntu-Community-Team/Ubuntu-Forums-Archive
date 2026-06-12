---
title: "Ubuntu 9.04 won't successfully reboot"
date: 2009-05-12
forum: General Help
---

### Post by Tonkenna on 2009-05-12
.... without booting to recovery mode and carrying out a file system check.
 
If I try to boot normally I can input name/password, then the machine hangs at a messy/distorted graphic. I have to hard reset to move on.
 
It's an Advent 4213 2Gb netbook running 9.04 desktop, updated from 8.10, dual boot with XP Home. 
 
It was pretty much fine after the update, except for the hibernation problem, which neccessitated rebooting to recovery mode to correct.
 
Any thoughts? Its getting a bit tedious having to do the file system check every time I switch it on.
 
P.S. also, why would the function key be permanently on? I mean the keyboard responds as if the FUNC key was pressed all the time.....
 
Cheers,
 
Phil

---

### Post by adamitj on 2009-05-12
The first problem (graphics error after boot) might be your video card drivers. Did you installed some drivers from "Restricted Drivers" menu? What's the vendor of your video card (nVidia, ATI, Intel)?

I don't know exactly, but the other problem maybe this is the messy ACPI issue.

I have a HP Pavilion dv6000 series notebook running 9.04 32-bit, and every time it enters hibernate mode I can't return to normal mode, only doing a hard reset.

A workaround I use is to edit /boot/grub/menu.lst file setting parameter "acpi=noirq" at the end of kernel line. It might appear like this:

```
title		Ubuntu 9.04, kernel 2.6.28-11-generic
uuid		948f7fe7-276e-4043-b135-95cec238fd92
kernel		/vmlinuz-2.6.28-11-generic root=UUID=1888f2c8-f6d6-46a5-9fe1-352227cd88c1 ro quiet splash acpi=noirq
initrd		/initrd.img-2.6.28-11-generic
quiet

```

This disables some functions in my notebook (like hibernation) and prevents from freezing at boot when in battery power mode.

---

### Post by Tonkenna on 2009-05-13
Thanks for the reply.
 
It's nvidia graphics and Intel 945 - there have been reported problems with this, but it was all working well for about a week from clean install. I guess something I've added via synaptic must be doing it.
 
I tried modifying the menu.lst file as you suggested, all that happened was that the distorted graphic had a different pattern!
 
During one of the successful boots, I removed a couple of '-bad' modules/plugins/things, but again, to no effect. I did, however, notice a reference to 'restricted drivers' as the boot scrolled past.
 
I'll check again that I haven't any drivers from the 'restricted' menu installed.
 
Cheers,
 
Phil

---

### Post by kryptikos on 2009-05-13
Need to see what the log files are saying once you actually have the box up and running. If you can post the contents of "dmesg" and look through /var/log/messages, might help us track down the right path.

---

### Post by Tonkenna on 2009-05-22
Well, after a lot of mucking about, removing s/w with no effect, the thing which stopped the problem in the end was reverting back to the KDE desktop from GNOME (I think).
 
Would that make any sense? Thanks for your replies, much appreciated.
 
Regards,
 
Phil

---

