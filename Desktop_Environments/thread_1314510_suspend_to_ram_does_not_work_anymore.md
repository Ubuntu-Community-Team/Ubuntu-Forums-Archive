---
title: "suspend to ram does not work anymore"
date: 2009-11-04
forum: Desktop Environments
---

### Post by zebul on 2009-11-04
hi.
I upgraded one box to **ubuntu 9.10**. it works nice (except the boot is slower)

I tried **suspend to ram** and it worked except when I woke up the pc, the *usb wifi key* was not working and I had to unplug-replug it to make it work again. I found that by using a file in /etc/pm/config.d with SUSPEND_MODULES="$SUSPEND_MODULES rt73usb".
it worked !

I tested several times and was quite happy it simply worked.

then I tried hibernate. it failed with a black screen after resuming.

and **now**, **[SIZE="3"]suspend to ram[/SIZE]** does not work anymore. the pc goes to suspend with a flashing led on the box. but when I woke it up, the bios began a normal boot process, instead of waking up straight to the desktop. as if it does not know it is in suspend mode.

so something has been changed and I can't track what.

how could I make suspend to ram work again ? (make it work at resume time)
how could I optionaly make hibernate work too ? (avoid the black screen)
and make the 2 play nice together ?

---

### Post by zebul on 2009-11-05
hourray **windows** hourray. :lolflag:

so i used windows to fix this.
simply rebooted into windows, **suspend to ram in windows**, resume it, rebooted, and suspend to ram worked in linux again.

something wrong in the BIOS ?? or ACPI ?? i don't know...

---

