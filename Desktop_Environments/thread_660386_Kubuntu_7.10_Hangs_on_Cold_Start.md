---
title: "Kubuntu 7.10 Hangs on Cold Start"
date: 2008-01-06
forum: Desktop Environments
---

### Post by lazylogic on 2008-01-06
PC Specs - New computer, Core 2 Dual, 3GHz, Nvidia 7500

Install Kubutnu 7.10 and working okay.

Shutdown the computer and let it rest for a couple of minutes.
Start the computer and tried to boot into Kubuntu.

After the grub screen, received
> 
Starting up ....
[   45.118469] pnp:  PnPACPI : METHOD_NAME_CRS failure for PNP0c01

and hangs at this screen.

Hard reset and reboot, after grub screen, this message will still be seen and disappear and will move on with the boot process.

Debian (on the same computer) is also reporting this message but will allow the boot process to go through (will not hang computer).

Any idea what is happening?

---

### Post by gilf on 2008-01-06
Maybe try booting with the grub boot option acpi=off to see if acpi is the problem.

If so, check to see if there is a BIOS upgrade for your computer. Occasional discovered specific ACPI incompatibilities in BIOS are cause for motherboard manufacturers to issue BIOS upgrades.

Look up "Boot Options"  in Ubuntu Community Documents if you don't know what they are.

Look up Bios upgrades on your computer manufacturer's website to see what is available, and how to apply them.

---

### Post by ubtpenguin on 2008-01-09
I am experiencing same problem on HP pavilion S3200T desktop 
my error is combined with 
dmi_string out of memory 
dmi_save_oem strings_devices out of memory
PnP ACPI METHOD_NAME_CRS failure for PNP0c01

then computer doesn't go further and rather restart 3 to 4 times 
then go into boot process....

It will eventually boot but it will reboot from that point 3 to 4 times. 

My system has Core 2 Duo processor with 3 GB Memory 

I am using ubuntu 64 ...

---

### Post by ubtpenguin on 2008-01-09
Okay

While I was googling I found out for the reason for dmi_string errors

My desktop is HP S3200T slimeline. 
Most of HP desktops experiencing this error and I saw one e-mail list saying about bug fix for this error. Hopefully this bug is fixed in upcoming kernel. 

But sill I couldn't find reason for PnP ACPI error. 
:rolleyes:

---

### Post by gilf on 2008-01-09
Did you try turning off ACPI through boot options?

Here's how:

[http://ubuntuforums.org/showthread.php?t=651659](http://ubuntuforums.org/showthread.php?t=651659)

---

### Post by ubtpenguin on 2008-01-10
Yes, I did try to stop ACPI support by using acpi=off option. 

It will remove PnP ACPI errors but it will not stop other errors. 

like dmi-string ... out of memory ... etc 

and it will reboot couple of times and then will really boot.

I am okay to live with it since eventually machine will boot after multiple reboot but kinda annoying. 

:lolflag:

---

