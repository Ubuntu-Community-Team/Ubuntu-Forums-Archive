---
title: "Ubuntu hangs at 'will now halt'"
date: 2006-09-29
forum: Desktop Environments
---

### Post by majabl on 2006-09-29
Evening, everyone.

I'm quite new to Ubuntu and things have been going pretty smoothly until recently, when my system has started hanging when I shut it down.

Everything goes as expected as far as 'Will now halt', at which there's a sound which sounds like the hard discs turning off but the system itself stays on.  I'm not sure what would cause this because I haven't been tinkering with any settings, but it seems to have coincided with v27 (or whatever that number refers to) of 6.06 appearing on my grub screen.  In the past, this computer would automatically switch off when shut down.

Perhaps also worth mentioning is that the system reboots just fine and that there are no issues there.

Thanks in advance!

Matthew

---

### Post by thephantomlinguist on 2006-09-29
Sound like you've got an ACPI problem.

I had the same problem a couple of years ago with a machine at work. It was a Dell Optiplex SX280 (nice machine). Turned out the memory that Dell had installed was incompatible(?) with the way Ubuntu handles ACPI. Or something like that. I really don't know much about it and I never could get it to work--just had to deal with holding down the power button until it would turn off after Ubuntu had shut down. SuSE had no problem though.

Not very helpful, I know, but it might give you a leaping off point...

Hope this helps!

---

### Post by wpshooter on 2006-09-29
Have you tried booting to a previous version of the Ubuntu/Linux kernel on the GRUB to see if this problem recurs on previous versions ?

If it does not, then perhaps there is a problem with the latest kernel but otherwise perhaps you have a hardware/machine problem.

Good luck.

---

### Post by doobit on 2006-09-29
> **thephantomlinguist said:**
> Sound like you've got an ACPI problem.

I had the same problem a couple of years ago with a machine at work. It was a Dell Optiplex SX280 (nice machine). Turned out the memory that Dell had installed was incompatible(?) with the way Ubuntu handles ACPI. Or something like that. I really don't know much about it and I never could get it to work--just had to deal with holding down the power button until it would turn off after Ubuntu had shut down. SuSE had no problem though.

Not very helpful, I know, but it might give you a leaping off point...

Hope this helps!

Some machines have both APM and ACPI, I think, and that causes a little conflict that you have to sort out. I fixed it by putting acpi=force in the boot command line in GRUB.

---

### Post by cotcot on 2006-09-29
This is a known bug.
When you see that message it is safe to switch off the power of the computer. You will not loose anything. 
I had it when i installed the i686 after the i386 kernel.
An alternative is to uninstall i686 and continue with i386.

---

### Post by majabl on 2006-09-30
> **cotcot said:**
> This is a known bug.
When you see that message it is safe to switch off the power of the computer. You will not loose anything. 
I had it when i installed the i686 after the i386 kernel.
An alternative is to uninstall i686 and continue with i386.

I tried booting with the i386 kernel but the same problem occurs.  Should this have happened, or is it the act of uninstallation of the i686 kernel that makes the difference?

If so, what's the best way for me to go about uninstalling the i686 kernel?  I forget how I installed it but I think it was the conventional route.

Ta!

---

### Post by majabl on 2006-10-27
Just to wrap this thread up, I uninstalled the i686 kernel and all was fine again.

---

