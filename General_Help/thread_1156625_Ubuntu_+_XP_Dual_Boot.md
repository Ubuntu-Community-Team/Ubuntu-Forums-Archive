---
title: "Ubuntu + XP Dual Boot"
date: 2009-05-11
forum: General Help
---

### Post by FallFromINFINITY on 2009-05-11
Ok, I've got Ubuntu 8.10 installed on my computer on the primary master harddrive.
Currently that is the selected boot device.

I just installed Windows XP onto another harddrive, the primary slave.

I want to add the Windows XP partition onto the boot list.
And if at all possible, to force the boot list to show up at startup to manually choose every time what OS to boot into.

- OR - (but preferably not)

I can force the primary slave hdd, Windows, to boot instead of the Ubuntu.

What should I add to the boot.ini file to include Ubuntu on the boot list.

---

### Post by stuboo on 2009-05-11
I'm not 100% sure so you should probably wait for confirmation, but in the mean time you might want to read up on editing your...

/boot/grub/menu.lst

I did this exact thing earlier in the week except all my OS's were installed to the same disk.

Hope this helps,
Ryan

---

### Post by lindsay7 on 2009-05-11
In the terminal type "sudo fdisk -l"  and see what your drives and partitons look like. Post the results here.

Also type in the terminal "sudo gedit /boot/grub/menu.lst" and post that.

---

