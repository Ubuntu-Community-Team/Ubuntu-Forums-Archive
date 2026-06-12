---
title: "Copying windows to second drive"
date: 2009-02-10
forum: General Help
---

### Post by Trzone on 2009-02-10
I have an ntfs partition which contains windows on it. However my family needs more space, and this second drive would be the best option.  I know windows xp has various settings (boot.ini)  The partition would be the 1st partition on the second hard drive (hd1,0) ?
Anyhow, i know gparted has a copying functionality but i also need to modify GRUB, any suggestions?
Thanks

---

### Post by Trzone on 2009-02-10
Now i need some expertise
this is the current boot.ini

[boot loader]

timeout=3

default=signature(e61c0)disk(0)rdisk(0)partition(1)\WINDOWS

[operating systems]

signature(e61c0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

now, windows is now on the first partition of the second drive.

---

### Post by logos34 on 2009-02-10
Leave the boot.ini as it is.

Now edit windows entry in menu.lst [like this]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk").

Also, you might want to install windows bootloader to the MBR of the second drive ('bootrec /fixmbr' if vista, 'fixmbr' if XP), just in case you ever need to boot directly from it

---

### Post by Trzone on 2009-02-10
Here is the GRUB entry

#/dev/sdb1
title		Windows XP
root		(hd1,0)
savedefault
makeactive
map        (hd0) (hd1)
map        (hd1) (hd0)
chainloader	+1

The partition is number 1 on the second hard drive (slave)
however, it says press ctrl+alt+delete to restart because of a disk error....

Here is boot.ini

[boot loader]

timeout=3

default=signature(e61c0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

signature(e61c0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect

---

### Post by logos34 on 2009-02-10
> **Trzone said:**
> 

default=signature(e61c0)disk(0)rdisk(0)partition(2)\WINDOWS

Why did your change boot.ini?  You don't need to edit it as long as windows is the first partition on the new disk.  So you want:

> ...partition(1)...

---

