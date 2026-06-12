---
title: "Trying to use F6 Options"
date: 2012-11-18
forum: Desktop Environments
---

### Post by anon_private on 2012-11-18
I am testing Lubuntu 12.04 desktop as a livecd and so far am disappointed with the results. The Chomium browser crashes frequently, as does Lubuntu (in a panic).

I would like to try Lubuntu with th F6 options.

At the Try Lubuntu screen I press tab and at the bottom of the page I get a command line:

/casper/vmlinz initrd=/casper/initrd.lz file=/cdrom/preseed/lubuntu.seed boot=casper quit splash --

I placed acpi=off after the -- and the system crashed.

How can I input the options:

acpi=off
noapic
nodmraid
nolapic

Can you also explain the functions of these options?

Thanks

Ps. If it matters I am using a Dell Dimension E520 Desktop computer with 512MB (at present) of Ram

---

### Post by ramblinche81 on 2012-11-18
For manual entered commands, that is the right idea,, wrong location....type the commands of interest before the double dashes 

quiet splash   xxxxxxx   - - 

I would encourage replacing the quiet splash with your commands so you can see the boot load activity and know if/when/where the system hangs or picks up an error.

That said, I thought the F6 option pulls up a menu, and you can space bar or enter to mark with X , then ESC to back out of F6 menu then enter to process GRUB for a trial from LiveCD ?

If working from native GRUB, I don't think F6 is available, and it is manual entry as you are inquiring. 

Good luck

---

### Post by anon_private on 2012-11-18
Thank you

Is this correct:

...boot=casper acpi=off noapic nodmraid nolapic --

F6 has no effect

What is GRUB?

I will try and locate the meaning of acpi, etc.

Best wishes.

A

Ps. Any tips for increasing stability


UPDATE

I have just tried the above

The first attempt everything seemed to go well, all [ok], I got to the background screen but a frozen mouse and no disk at the top left hand corner.

I re-tried, again all went well and this time I got the full screen. On browsing to ubuntu forums everthing froze

Any advice regarding options, etc?

Thanks

---

### Post by ramblinche81 on 2012-11-23
> **anon_private said:**
> Thank you
 
Is this correct:
 
...boot=casper acpi=off noapic nodmraid nolapic --
 
F6 has no effect
 
What is GRUB?
 
I will try and locate the meaning of acpi, etc.
 
Best wishes.
 
A
 
Ps. Any tips for increasing stability
 
 
UPDATE
 
I have just tried the above
 
The first attempt everything seemed to go well, all [ok], I got to the background screen but a frozen mouse and no disk at the top left hand corner.
 
I re-tried, again all went well and this time I got the full screen. On browsing to ubuntu forums everthing froze
 
Any advice regarding options, etc?
 
Thanks
 
I am no expert, I am relying on suggestions from others to me.
 
Instead of turning OFF all the features at same time, ACPI, MODESET, APIC, LAPIC, DMRAID etc
 
Only turn off one at a time to get started.
 
ACPI is the power management and configuration tool. It shouldn't have to be turned off but it seems to help people get started/loaded so I would suggest leaving it ON if at all possible.
 
nomodeset is the command I didn't see included and it relates to the video graphics mode default. For blank or corrupted screens, that seems to be the cure all.
 
 
 Each machine is a little different based on BIOS and video graphics chipset which seems to be the source of most headaches.

Good luck, you will need to use the search function because above is the extent of my knowledge on 12.04, I've been on it for about a week !!!

---

