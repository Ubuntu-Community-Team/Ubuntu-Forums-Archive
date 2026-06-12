---
title: "Transform live-cd into live-hard..."
date: 2017-07-13
forum: Desktop Environments
---

### Post by bouzzi on 2017-07-13
I'm trying to set ubuntu on a thin client = 1Gb harddrive...

A desktop live-cd is less 800 Mb...

Is it possible to use to modify the live-cd image and write it down on the harddrive and use it?

I want it to boot directly to the "try ubuntu" without all the other software usually in place and starting automatically vmware horizon view....

Can we make it happened ?


Bouzzi

---

### Post by &amp;KyT$0P# on 2017-07-13
You might try making a custom live ISO without any ubiquity packages installed.

See [this]("https://help.ubuntu.com/community/LiveCDCustomization") to get started with customising live CDs.  If you need to be able to EFI-boot the system, when you're ready to actually create the new ISO follow [these steps]("https://linuxconfig.org/legacy-bios-uefi-and-secureboot-ready-ubuntu-live-image-customization#h5-creating-a-boot-able-isohybrid-iso-image") instead of the [FONT=Courier New]mkisofs[/FONT] command.


Also, just to point out - in the live environment, [FONT=Courier New]sudo[/FONT] doesn't require any password.  Not sure if that would be problematic for you.

---

