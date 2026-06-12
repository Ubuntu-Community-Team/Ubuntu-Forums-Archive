---
title: "Oh oh, I broke something"
date: 2007-04-05
forum: Desktop Environments
---

### Post by frankerooney on 2007-04-05
Right, 
well I was messing about trying to get ubuntu edgy to boot a bit quicker by turning off some of the services, including acpi. I found out after reboot that I probably need that service, but ever since I enabled it again, my battery status just shows "AC POWER". I've had a look in /proc/acpi/battery, and I've got two folders - C16C, and C16D. The C16D folder has info about the battery, so I assume the applet is looking for the wrong files? How do I fix it?!!

oh, by the way, does anyone have a good alternative to gdesklets - just installed vista on my work pc and find the sticky notes gadget really useful. The one on gdesklets is not as good as you can't just click on it and type - have to edit text line by line! not great..
Cheers.

---

### Post by Spr0k3t on 2007-04-05
> **frankerooney said:**
> oh, by the way, does anyone have a good alternative to gdesklets - just installed vista on my work pc and find the sticky notes gadget really useful. The one on gdesklets is not as good as you can't just click on it and type - have to edit text line by line! not great..
Cheers.

You may want to have a look at tomboy.  It's a new addition to Feisty which seems pretty good.  Also, Screenlets seems to offer something in the way of sticky notes, but I'm not sure how well the implementation is.  Not a fan of sticky note systems... at least, I've not found a decent one yet.

---

### Post by frankerooney on 2007-04-05
Cheers - just checking out screenlets now - there is a postit note thing on it, and it looks pretty good. Will have a look at Tomboy aswell.

anyone got any ideas on my battery thing?

---

### Post by frankerooney on 2007-04-05
Don't know if this is worth adding, but hal-device-manager can't see my battery at all - is gnome-power-manager dependent on info from the HAL?

---

### Post by frankerooney on 2007-04-05
ok, in case it helps someone, I found an answer here:
[http://ubuntuforums.org/showthread.php?t=321221&highlight=hal+no+battery]("http://ubuntuforums.org/showthread.php?t=321221&highlight=hal+no+battery")
by changing the name of the S50acpid entry in rc2.d it started the acpi daemon before the hal one, which sorted the status out.
Cheers.
Frankerooney.

---

