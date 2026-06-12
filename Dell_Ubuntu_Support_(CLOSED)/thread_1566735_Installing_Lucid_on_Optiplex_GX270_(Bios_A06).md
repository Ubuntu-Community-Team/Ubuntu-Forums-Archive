---
title: "Installing Lucid on Optiplex GX270 (Bios: A06)"
date: 2010-09-02
forum: Dell Ubuntu Support (CLOSED)
---

### Post by paingwinn on 2010-09-02
Attempted to install Lucid on an Optiplex GX270 with vA06 BIOS.

Installation via CD crashed about 10% in. 

This apparently blasted the HDD back to the stone age since further attempts to install from the Lucid CD and the alternate installer can't seem to find the HDD. 

I get the sense that if I could just get something to see the HDD and allow me to reformat/repartition, then I should be okay and at least I could maybe use the alternate installer to complete the installation. 

It's status right now? After POST I get: 

[INDENT]LINUX 4.0 4.0-pre46 ETCD Copyright (Etc. etc.)
{unreadable)ing sectors error(EDD)
ERROR: No configuration file found[/INDENT]

Help?

---

### Post by mörgæs on 2010-09-04
Can you see the condition of the drive, if you boot a live Knoppix?

---

### Post by paingwinn on 2010-09-07
Thanks for getting back to me.

> **mörgæs said:**
> Can you see the condition of the drive, if you boot a live Knoppix?

I can see it mounted to /media/sda1 in Knoppix, listed as "38.5GB Volume." When I boot up, however, POST gives me the double-beep and says "SATA Primary drive 0 not found. STrike the F1 key to continue, F2 to run the setup utility."

---

### Post by pricetech on 2010-09-07
The GX270 BIOS is up to A07.  I'd upgrade and see if that helps.  You can easily do that from a DOS floppy.

Reset the BIOS to defaults and let it find the drives again.  I usually remove the battery on those older Dells when I encounter them.

Once the BIOS has found the drive again, run the Hard Drive Diagnostic, available from the boot menu.  F12 will get you there.

---

### Post by Baji P. on 2010-09-07
I am currently running a GX270, but using Karmic. I am not sure that your issue is Linux/Ubuntu related.

GX270 has two IDE & one Sata ports. Is your HD sata or IDE ? Go into bios and make sure the appropriate boot device is enabled, and any boot devices that don't exist are not in the boot sequence.

I think the current bios is A07, you are close enough that it shouldn't matter.

Your ~ 40Gig HD should also be easily managed. My drive is 320 Gig and it recognized fine.

---

### Post by paingwinn on 2010-09-07
> **Baji P. said:**
> GX270 has two IDE & one Sata ports. Is your HD sata or IDE ? Go into bios and make sure the appropriate boot device is enabled, and any boot devices that don't exist are not in the boot sequence.

It's a SATA HDD. The boot sequence is CD then HDD. The BIOS keeps referring to the HDD as an "unknown device."

---

### Post by Baji P. on 2010-09-07
Do you have a spare hdd that you can try with ? I am pressed for time, or else I would have tested 10.04.1 on a spare GX270 & given you a few more suggestions.

---

### Post by pricetech on 2010-09-13
> **paingwinn said:**
> It's a SATA HDD. The boot sequence is CD then HDD. The BIOS keeps referring to the HDD as an "unknown device."

Have you upgraded the BIOS and reset to defaults ??

The diags won't run if the computer doesn't know what it is.

---

