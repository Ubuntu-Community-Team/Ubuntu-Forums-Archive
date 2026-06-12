---
title: "BIOS upgrade on Vostro 1310"
date: 2008-07-28
forum: Dell Ubuntu Support (CLOSED)
---

### Post by neur0 on 2008-07-28
There is a BIOS update for my laptop in .exe form on [http://support.dell.com](http://support.dell.com)

I cannot seem to upgrade my BIOS. Here is what I've tried so far:

firmware-tools (from wiki [https://wiki.ubuntu.com/DellBIOS](https://wiki.ubuntu.com/DellBIOS))
It says there are no updates. (my firmware is A05, new one is A10)

I would have tried using libsmbios
(tutorial from [http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate](http://linux.dell.com/wiki/index.php/Tech/libsmbios_dellBiosUpdate))
But there is no 0x026 (my system ID) folder in bios headers directory
([http://linux.dell.com/repo/firmware/bios-hdrs/](http://linux.dell.com/repo/firmware/bios-hdrs/))

So I finally tried using biosdisk
([http://linux.dell.com/projects.shtml](http://linux.dell.com/projects.shtml))
And everything is going fine, but when I boot to the image DOS prompt, it says "bad command or file name" then I try  <firmware>.exe to manually start it but I get the "cannot run in DOS mode" error.

---

### Post by lisati on 2008-07-28
I suspect that you might need to run your BIOS upgrade from within Windows.

---

### Post by neur0 on 2008-07-28
I DO have my old WinXP cd, and I have tried using BartPE to install it, however, the BartPE environment does not provide the C: partition and the install needs to extract some temp files there I guess. There is a message that I should change the path, but its grayed out, so I believe I can't do it with BartPE.

---

