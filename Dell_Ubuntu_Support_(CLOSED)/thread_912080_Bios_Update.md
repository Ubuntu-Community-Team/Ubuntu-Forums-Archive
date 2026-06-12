---
title: "Bios Update"
date: 2008-09-06
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Denny Johnson on 2008-09-06
I have a 1420n that I recently updated from 7.04 to 7.10 and then 8.04.
All seems OK except some resume from suspend issues:
- no backlight
- often no wifi, apparently network disabled.
When I boot, I see that my Bios is A01.
Over at Dell, it looks like A09, 7/14/08, is available [and recommenced] for download for 1420.
Is the Bios the same for 1420 and 1420n?
Anything I need to do before downloading the A09 Bios?
Is there a tutorial re how to do this?
Thanks

---

### Post by anjilslaire on 2008-09-06
According to [http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx]("http://direct2dell.com/one2one/archive/2008/07/25/nvidia-gpu-update-for-dell-laptop-owners.aspx"):

> 
heinzoel said:

Bios-Update on Ubuntu without boot-disk:

- install libsmsbios-bin

- 'sudo getSystemId' , notice ID (for example 0x01BD)

- download bios.hdr from the matching folder under ' [http://linux.dell.com/repo/software/bios-hdrs/](http://linux.dell.com/repo/software/bios-hdrs/)'

- sudo modprobe dell_rbu

- sudo dellBiosUpdate -u -f ./bios.hdr

- reboot


Also check this thread:
[http://ubuntuforums.org/showthread.php?t=877611&highlight=1420+heat&page=2]("http://ubuntuforums.org/showthread.php?t=877611&highlight=1420+heat&page=2")

Finally, check the [Dell Ubuntu Wiki]("http://linux.dell.com/wiki/index.php/Ubuntu_8.04")

---

