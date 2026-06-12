---
title: "power down vs. unplugging"
date: 2009-06-04
forum: General Help
---

### Post by meg23 on 2009-06-04
I have an old Pentium II  desktop that does not seem to support "shutdown -p now" (complete power off) or sleep. When I do type "shutdown -p now" it it pauses for a few moments prompts "System has halted, safe to power off or press any key to reboot." My idea was to set up a timer to turn off the computer after the system halted and use the loss of power feature to restart the computer once power is restored. Is turning off a halted computer with the power button or unplugging it from the power any different?

---

### Post by spcwingo on 2009-06-04
Shutting down by the power button just kills the juice to everything after the power supply.  Pulling the cord kills everything including the power supply.

BTW, have you tried:

```
acpi=force
```

in the kernel line of your /boot/grub/menu.lst?  That might allow it to auto-shutdown.

---

### Post by rax_m on 2009-06-04
Have you tried "shutdown -h now"
h = halt

---

### Post by khelben1979 on 2009-06-04
> **meg23 said:**
> Is turning off a halted computer with the power button or unplugging it from the power any different?

The main difference with this is that many powersupplies continues to draw power (way less than when the computer is powered on off course) even when you have powered it down with the off button until you press the off switch at the back side or draw out the power cable.

---

### Post by meg23 on 2009-06-04
"shutdown -h now" results in the same thing as "shutdown -p now". As far as I can tell although some type of powersaving is possible in the BIOS, I assume that it is not acpi but apm, but alas apm doesn't seem to work either. Considering I found the computer in the trash, I figured something might be broken in it. What I really want to achieve is to have the computer turn on on at a certain time and turn off at a certain time. Any other ideas? Would pulling the plug after the system is halted damage the computer?

---

### Post by tomski on 2009-06-04
check your bios setting as i used to use an old DELL Optiplex G100 which had a neat thing in the bios where i could set the power button to behave like a keyboard power off button!!

also try different acpi settings in the BIOS but make sure you have a backup first

it maybe that your mobo has a few quirks 

most BIOS do support auto on & off as again with the old optiplex i used had this same feature which i had set to auto power on at 0100 just incase of powercut etc then put the box in the attic and left it lol

if your mobo does not support these you get a external timer which plugs into the power feed socket & then you plug whatever device into the timer then you just set the timer to do what you want at what ever time you want
so it would look like this:

Power Socket-|<--Timer Socket-|<--PC-

---

### Post by meg23 on 2009-06-04
Tomski: When your say timer socket...do you mean a standard wall outlet timer? If so, thats basically what I was talking about doing.

If its of any help, its a Pentium II Nec Powermate 5100

---

### Post by tomski on 2009-06-04
yup that is it
the sort you would use for erm growing plants etc :)

---

### Post by meg23 on 2009-06-04
That would not damage the machine provided that it has halted?

---

