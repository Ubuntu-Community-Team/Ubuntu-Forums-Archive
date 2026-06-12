---
title: "drivers for devices for kubuntu"
date: 2006-05-31
forum: Desktop Environments
---

### Post by rbprogrammer on 2006-05-31
ok, so i have two devices that i have that need to be able to be used from kubuntu. i really hate having to reboot into my windows partition every time i have to use the devices. any help for either one would be greatly appreciated...

the first device is my printer, i have a Dell AIO 922.  i've tried looking for the drivers and whatnot, and i found that my printer was remarked (or whatever) to some lexmark brand of printers.

the second device is my mp3 player, a Dell DJ 30GB.  i get the feeling that kubuntu recognizes the device, its just that i dont have software to work with this device.  i get this feeling because i used the command [FONT="Courier New"]lsusb[/FONT]. before i plug in the mp3 player, i get this for the output:
[INDENT]Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 413c:5109 Dell Computer Corp.
Bus 001 Device 003: ID 046d:c509 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000[/INDENT]
and after i plug in the mp3 player i get this:
[INDENT]Bus 004 Device 006: ID 041e:4126 Creative Technology, Ltd
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 413c:5109 Dell Computer Corp.
Bus 001 Device 003: ID 046d:c509 Logitech, Inc.
Bus 001 Device 001: ID 0000:0000[/INDENT]

i might be wrong, but i just think i dont have software for the mp3 player. and for the printer, its not even recognized in the system settings for printers. so again, any help is greatly appreciated...

---

### Post by catlett on 2006-05-31
Search for lexmark X5270 in the printer drivers section. They are the same.
 Got this from a link in this thread
 (at the bottom)[http://www.linuxquestions.org/hcl/showproduct.php?product=2074&cat=myprod](http://www.linuxquestions.org/hcl/showproduct.php?product=2074&cat=myprod)

---

### Post by ltmon on 2006-05-31
Drivers for the Dell DJ do exists for linux, as it's mainly a rebrand of the Creative Zen.

I don't know exactly but try installing the package "kzenexplorer" and see it that can deal with it.

L.

---

### Post by amanda on 2006-07-10
My searches for lexmark X5270 drivers only led me to discussions of how they supposedly work for the aio 922. I didn't actually find any linux drivers for the Lexmark either.

---

### Post by altonbr on 2006-09-24
I know this is 5.10 and I'm using 6.06 but CUPS for Kubuntu still doesn't have the Dell AIO 922 nor the Lexmark x5270.

Can anyone help? Is there a bigger list of drivers that I can choose from somewhere?

---

