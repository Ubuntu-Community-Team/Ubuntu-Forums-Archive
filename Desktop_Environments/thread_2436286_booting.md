---
title: "booting"
date: 2020-02-03
forum: Desktop Environments
---

### Post by mikelhayes on 2020-02-03
howdy,
I'll post my grub menu (IF I CAN POST HERE AT ALL)

everytime my pc reboots it goes to a generic 19.04 instead of my 1910 desktop..

---

### Post by oldfred on 2020-02-03
Did you update or do a new side by side install, so you have two installs?

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) & 
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

### Post by mikelhayes on 2020-02-03
[ATTACH=CONFIG]284961[/ATTACH][ATTACH=CONFIG]284962[/ATTACH]

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT="Ubuntu 19.10 (19.10) (on /dev/sda2)"
GRUB_TIMEOUT_STYLE="hidden"
GRUB_TIMEOUT="5"
GRUB_DISTRIBUTOR="`lsb_release -i -s 2> /dev/null || echo Debian`"
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to enable BadRAM filtering, modify to suit your needs
# This works with Linux (no patch required) and with any kernel that obtains
# the memory map information from GRUB (GNU Mach, kernel of FreeBSD ...)
#GRUB_BADRAM="0x01234567,0xfefefefe,0x89abcdef,0xefefefef"

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL="console"

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE="640x480"

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID="true"

# Uncomment to disable generation of recovery mode menu entries
#GRUB_DISABLE_RECOVERY="true"

# Uncomment to get a beep at grub start
#GRUB_INIT_TUNE="480 440 1"

GRUB_SAVEDEFAULT="false"
#GRUB_DISABLE_OS_PROBER="false"
```

---

### Post by mikelhayes on 2020-02-03
FIXED. Good call.
Thank you

---

### Post by wildmanne39 on 2020-02-03
Glad it is working please use thread tools at the top of the page to mark the thread solved and post the solution so the whole community can benefit from your solution.

Thanks

---

