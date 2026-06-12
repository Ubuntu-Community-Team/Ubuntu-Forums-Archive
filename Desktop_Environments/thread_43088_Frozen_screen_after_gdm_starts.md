---
title: "Frozen screen after gdm starts"
date: 2005-06-20
forum: Desktop Environments
---

### Post by bungilo on 2005-06-20
using a Proliant 1850R, 3 9.1GB scsi disks in a aggregated array with onboard ATI Mach64 Rage IIc.  Used Hoary install disk but on boot there was no screen.  Messed around with Xorg.conf to no avail so thought I would uninstall and install XFree86 since I've had better luck with it (have 3 other linux boxes running knoppix 3.x).  Still no screen.  Decided to run the warty live cd and copy its XF86Config-4 over to the hoary install /etc/X11.  Finally got a gui to appear (basically the earth background); frozen mouse and keyboard is locked not allowing CTRL+ALT+F1 to go to text mode.  Also screen is only part of the monitor (about 2/3 of it).  Using acpi=off vga=normal nosound noapic nodma noapm nousb nofirewire nopcmcia noagp nomce nodhcp xmodule=vesa and using vesa instead of ati driver in config (what warty live-cd chose and it works fine).  I set up gdm to log for debugging but there are no errors other than fonts not found.  Tried adding nofb or framebuffe=false to grub boot parameters but did nothing but show 'frozen static' at the graphical screen.  I did apt-get -f install to fix any dependencies and did dpkg-reconfigure gdm and apt-get install --reinstall gdm.  Any ideas?

---

### Post by Alexander Kirillov on 2005-06-21
[QUOTE=bungilo]using a Proliant 1850R, 3 9.1GB scsi disks in a aggregated array with onboard ATI Mach64 Rage IIc.  Used Hoary install disk but on boot there was no screen.  Messed around with Xorg.conf to no avail so thought I would uninstall and install XFree86 since I've had better luck with it (have 3 other linux boxes running knoppix 3.x).  Still no screen.  Decided to run the warty live cd and copy its XF86Config-4 over to the hoary install /etc/X11.  Finally got a gui to appear (basically the earth background); frozen mouse and keyboard is locked not allowing CTRL+ALT+F1 to go to text mode.  Also screen is only part of the monitor (about 2/3 of it).  Using acpi=off vga=normal nosound noapic nodma noapm nousb nofirewire nopcmcia noagp nomce nodhcp xmodule=vesa and using vesa instead of ati driver in config (what warty live-cd chose and it works fine).  I set up gdm to log for debugging but there are no errors other than fonts not found.  Tried adding nofb or framebuffe=false to grub boot parameters but did nothing but show 'frozen static' at the graphical screen.  I did apt-get -f install to fix any dependencies and did dpkg-reconfigure gdm and apt-get install --reinstall gdm.  Any ideas?[/QUOTE]
 Using Hoary with XFree86 is possible, but not easy. I'd suggest trying to get xorg to work...

---

