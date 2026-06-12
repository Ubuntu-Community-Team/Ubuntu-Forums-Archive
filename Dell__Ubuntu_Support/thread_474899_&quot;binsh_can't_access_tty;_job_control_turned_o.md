---
title: "&quot;/bin/sh: can't access tty; job control turned off&quot;"
date: 2007-06-15
forum: Dell  Ubuntu Support
---

### Post by onemustfall on 2007-06-15
"/bin/sh: can't access tty; job control turned off" 

I'm getting this error while trying to boot from DVD. I'm using v7.04 that I recieved from the cover of Linux Format magazine.

My PC specs:

Dell Dimension 2300
Intel Pentium 4 2.60GHz
1GB RAM
(Windows XP Home SP2)

I've tried:

- Booting in "Safe Graphics Mode"
- Pressing F6 at start up then using "noapic"
- F6 + break=top then at pause "modprobe piix", then exit. This creates a infinate loop.

HELP!

---

### Post by onemustfall on 2007-06-15
*UPDATE*

I've tried the following:

-F6 + acpi=off
-F6 + removing splash, quiet, and -- then adding noapic
-F6 + removing splash, quiet, and -- then adding break=top
-F6 + removing splash, quiet, and -- then adding all_generic_ide
-F6 + removing splash, quiet, and -- then adding modprobe piix

With some (bottom two) of these I get a little thurther but then I get the following error:

I/O error, dev fd0, sector 0

Do you think it could be a problem with my graphics card. PCI NVIDIA GeForce FX 5200 256mb?

---

### Post by neptho on 2007-06-15
fd0 is floppy; do you have a floppy drive attached?

---

### Post by fluteflute on 2007-06-16
I've fixed this on a Dell 4300 by simply placing a floppy in the floppy drive.

---

### Post by onemustfall on 2007-06-16
*UPDATE*

I do have a floppy drive attached. Do I need to unattach it? Or is there a workaround?

I've tried:

-F6 + removing splash, quiet, and -- then adding modprobe piix and inserting a floppy disk. This gives me the following: agpgart: AGP aperture is 128 @ 0xe0000000. Then it freezes.

-F6 + removing splash, quiet, and -- then adding all_generic_ide and inserting a floppy disk. This gives me the following error: I/O error, dev fd0 sector 0.

Thank you.

---

