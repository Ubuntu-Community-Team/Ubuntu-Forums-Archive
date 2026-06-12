---
title: "[SOLVED] How do I change the Boot Drive"
date: 2009-01-03
forum: Desktop Environments
---

### Post by alexham on 2009-01-03
I have 2 HDs, an IDE and a SATA. The system defaults to IDE at boot unless I press F8 and select SATA drive. Then the bootloader appears and defaults to Ubuntu. But if I am not quick enough to press F8, it starts in Windows, so I have to restart and try again.

The SATA drive does not appear as a boot option in Bios.

I know that it is possible to select the SATA drive as the 1st boot device, but I have forgotten how to do it and the present arrangement is very annoying.

Can anyone help, please?

Thanks,

Alex

---

### Post by caljohnsmith on 2009-01-03
By pressing F8, it sounds like you are getting your BIOS's boot menu where you choose which drive to boot from, but if you want to permanently boot the Ubuntu drive on start up, you'll need to figure out how to get into your BIOS settings and change the "boot order". Probably some other function key will take you to all your BIOS settings, but it varies depending on your motherboard. Good luck and let me know how it goes.

---

### Post by alexham on 2009-01-03
> **caljohnsmith said:**
> By pressing F8, it sounds like you are getting your BIOS's boot menu where you choose which drive to boot from, but if you want to permanently boot the Ubuntu drive on start up, you'll need to figure out how to get into your BIOS settings and change the "boot order". Probably some other function key will take you to all your BIOS settings, but it varies depending on your motherboard. Good luck and let me know how it goes.

You are right! Pressing F8 gives me a list of drives and a choice from which to boot.  Pressing <Delete> when the Bios menu is on the screen gets me into Bios where I can set permanently the 1st boot drive, but until now the drive on which I have Ubuntu was not there because it was disabled.

I have just enabled it and now the system boots into Ubuntu automatically, which is the way I prefer it.

Thanks,

Alex

---

