---
title: "[SOLVED] Kernal updated - two options at GRUB upon boot..."
date: 2009-01-01
forum: General Help
---

### Post by OinkOink2 on 2009-01-01
Hi all,

I have two Ubuntu Kernels showing at the GRUB bootloader since the kernel was updated.

Do I have to "uninstall"/remove the older kernel? Or simply delete the entry in grub config file?

If the former could you please advise?

OinkOink2.

---

### Post by oilchangeguy on 2009-01-01
> **OinkOink2 said:**
> Hi all,

I have two Ubuntu Kernels showing at the GRUB bootloader since the kernel was updated.

Do I have to "uninstall"/remove the older kernel? Or simply delete the entry in grub config file?

If the former could you please advise?

OinkOink2.

this is normal. you can delete it if you want to. many leave it, in case of problems with the new kernel. you can still boot the computer.

---

### Post by OinkOink2 on 2009-01-01
Right, thanks.

---

### Post by adult swim on 2009-01-01
alot of people leave the two kernels there so if the new one happens to fail, they can fall back on the old one which is known to work.  it boils down to your personal preference.   you can delete the old one in grub, or you can comment it out.  if you want to remove the kernel you can search for 'linux-image' in synaptic package manager and select the old one for removal.  make sure and not remove the one you are using now!  if you are unsure of which is which, if you go to a terminal and enter in ```
uname -r
``` it will show you which kernel you are currently running.

---

### Post by drs305 on 2009-01-01
Here's a HOWTO if you want to learn more about your display options and a gui app that can edit menu.lst without having to edit it manually:
[URL="http://ubuntuforums.org/showthread.php?t=818177"] HOWTO: Grub Menu Kernel Display Options
[/URL]

---

