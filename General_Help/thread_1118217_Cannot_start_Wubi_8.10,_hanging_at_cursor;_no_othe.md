---
title: "Cannot start Wubi 8.10, hanging at cursor; no other solutions helped"
date: 2009-04-06
forum: General Help
---

### Post by Archoniam on 2009-04-06
OK, since nobody has answered me anywhere else, I hope someone at the forums here can help:
My 8.10 Wubi installation will not start. I installed using all methods, but no matter what, when I try to boot any kind of Linux, some problem happens. Even LiveCDs. For Ubuntu, which I'm mostly trying to use, it just hangs at startup with a blinking cursor. I have to run it with ACPI workarounds just to get it to work, I suspect by that this has something to do with my ACPI. But when I do the ACPI workaround option, too, it stops on another command line about 120 seconds in, i think it involved my SATA drive... I'm still working on trying to not dual boot on one drive, but hook up my old 80gig drive for Linux, and there's been no success. Does anyone know a possible solution for this?

Thanks in advance, hope I can find help soon.:mad:

---

### Post by timClicks on 2009-04-08
can you enter the output of ```
startx
``` into the shell?

---

### Post by StarryKnight on 2009-04-08
i'm too encountering the same problem with 8.04 LTS. Haven't tried 8.10 though.
when in live cd mode, it starts up only rarely without any workarounds (but at least did sometimes and also did start up after applying the acpi=off, 

but after i installed ubuntu today with the install ubuntu inside windows option, it just fails to startup, windows works normally though. 

all i get after selecting ubuntu from the bootloader is a line "Press esc for menu 3...2...1, and then a blinking cursor :frown:

even after i press esc, and select the acpi workaround or even the safe graphics mode, the same thing happens (while it always worked with the acpi=off option in live mode).

**@timClicks** how to do that??

---

### Post by StarryKnight on 2009-04-08
Ok, so i tried to run the uninstaller from windows to start fresh, but the uninstaller exits as soon as it is run, and doesn't do anything! :(

Some details about my installation: Installed on a separate physical disk (Primary Slave), not on a partition of the windows disk. Given 4GB space.

What to do now, and how do i completely remove the existing installation and install maybe on a partition of the drive windows is installed on?

PS: i have a know how of editing the windows bootloader and editing the registry.
And strangely i can boot on live cd mode normally now (in fact i'm posting this from inside there :)), without any modifications... can someone please help us?

And now i can see two files wubildr and wubildr.mbr on both c:(windows system drive) and d:(where i installed ubuntu).

EDIT: I've sorted out the uninstallation issue. Should i install wubi on the same drive as windows (C:)??

---

### Post by StarryKnight on 2009-04-08
I finally got it working!! Manually uninstalled from d:, installed again on c: (the same as windows), and voila! its working without hitches :guitar:.

**@Archoniam** Maybe this would help you too?? Have you tried doing what i have done?

---

