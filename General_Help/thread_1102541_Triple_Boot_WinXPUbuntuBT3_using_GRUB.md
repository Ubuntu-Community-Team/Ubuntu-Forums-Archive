---
title: "Triple Boot WinXP/Ubuntu/BT3 using GRUB"
date: 2009-03-21
forum: General Help
---

### Post by The Sorrow on 2009-03-21
I recently installed GRUB to boot Backtrack3 on my laptop and am having trouble configuring the menu.lst file. I need to know what to enter to boot the BT3 kernel. With this setup i get a kernel panic error:

# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color black/cyan yellow/cyan
timeout 30
default /default

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root /ntldr
chainloader /ntldr
savedefault --wait=2

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda2.
title BackTrack3 (on /dev/sda2)
root (hd0,1)
kernel /boot/vmlinuz root=/dev/sda2 ro vga = 773
savedefault
boot


any suggestions?

---

### Post by The Sorrow on 2009-03-24
Ive made some progress, i managed to figure out the boot was on the wrong device so i set it up to:


# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color black/cyan yellow/cyan
timeout 30
default /default

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root /ntldr
chainloader /ntldr
savedefault --wait=2

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title BackTrack3 (on /dev/sda1)
root (hd0,1)
kernel /boot/vmlinuz root=/dev/sda1 ro vga = 773
savedefault
boot

but now i get 

Error 19: cannot mount partition:

so im led to ask for help yet again, can anyone push me in the right direction?

---

### Post by plucky on 2009-03-24
> **The Sorrow said:**
> Ive made some progress, i managed to figure out the boot was on the wrong device so i set it up to:


# This is a sample menu.lst file. You should make some changes to it.
# The old install method of booting via the stage-files has been removed.
# Please install GRLDR boot strap code to MBR with the bootlace.com
# utility under DOS/Win9x or Linux.

color black/cyan yellow/cyan
timeout 30
default /default

title find and load NTLDR of Windows NT/2K/XP
fallback 1
find --set-root /ntldr
chainloader /ntldr
savedefault --wait=2

# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/sda1.
title BackTrack3 (on /dev/sda1)
[color=red]root (hd0,1)[/color]
kernel /boot/vmlinuz root=/dev/sda1 ro vga = 773
savedefault
boot

but now i get 

Error 19: cannot mount partition:

so im led to ask for help yet again, can anyone push me in the right direction?

Should read as ```
root (hd0,0)
``` assuming sda1 is the correct partition.

Read all about [Grub](http://users.bigpond.net.au/hermanzone/p15.htm#page%20index)

Good Luck

---

