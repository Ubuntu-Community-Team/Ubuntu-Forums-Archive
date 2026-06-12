---
title: "grub2 menu is gone!"
date: 2009-12-17
forum: Desktop Environments
---

### Post by phillychease on 2009-12-17
i installed windows 7 on my computer, well double booted it and now my grub2 menu is gone.

i tired following instructions on this[ site]("https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD") but i got confused here 

[LIST]
[*]Now you need to edit the **/etc/default/grub** file to fit your system
[/LIST]
what do i do when i edit it? this is what i get:

```
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.

GRUB_DEFAULT=0
GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT="10"
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
GRUB_CMDLINE_LINUX=""

# Uncomment to disable graphical terminal (grub-pc only)
#GRUB_TERMINAL=console

# The resolution used on graphical terminal
# note that you can use only modes which your graphic card supports via VBE
# you can see them in real GRUB with the command `vbeinfo'
#GRUB_GFXMODE=640x480

# Uncomment if you don't want GRUB to pass "root=UUID=xxx" parameter to Linux
#GRUB_DISABLE_LINUX_UUID=true

# Uncomment to disable generation of recovery mode menu entrys
#GRUB_DISABLE_LINUX_RECOVERY="true"


```here are the fdisk info:

[html]Disk /dev/sda: 120.1 GB, 120060444672 bytes
255 heads, 63 sectors/track, 14596 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf84ef84e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        7135    57311856   83  Linux
/dev/sda2   *        7136        7148      102400    7  HPFS/NTFS
/dev/sda3            7148       14057    55497728    7  HPFS/NTFS
/dev/sda4           14058       14596     4329517+   5  Extended
/dev/sda5           14058       14596     4329486   82  Linux swap / Solaris
[/html]

---

### Post by Rmantingh on 2009-12-17
I'm not an expert but I don't think you need to edit this file in your case.
The default settings look OK to me.
You could increase the timeout if you want to keep the grub menu open a bit longer than the 10 seconds set in your file.
Simply continue with the next steps in the recovery process.

---

### Post by phillychease on 2009-12-17
> **Rmantingh said:**
> I'm not an expert but I don't think you need to edit this file in your case.
The default settings look OK to me.
You could increase the timeout if you want to keep the grub menu open a bit longer than the 10 seconds set in your file.
Simply continue with the next steps in the recovery process.

eh it doesnt work. i followed through the rest. i think i have to edit it.
any suggestions?

---

### Post by Rmantingh on 2009-12-17
Something that I noticed in your "fdisk -l" listing.
Your second partition is set to be the bootable partition.
Try setting the first partition to be bootable instead of the second one.
You can change this by booting into your LiveCD and running "fdisk /dev/sda" in a terminal.

In the fdisk menu press following keys (followed by ENTER):-
  m  - show available key actions
  p  - shows the current partitioning
  a  - starts toggle boot flag dialog
  1  - toggles (on) the boot flag for partition 1
  a  - starts toggle boot flag dialog
  2  - toggles (off) the boot flag for partition 2
  p  - shows the changed partitioning
  w  - write the new partitioning layout to disk

Reboot

---

### Post by hariks0 on 2009-12-18
hi, you should be able to reset Grub2 with Win here --> [http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

If it's borked your Grub2 installation totally, just re-install Grub2, it looks scary, but is a walk in the park, instead of scratching your head, trying different 'tweaks' --> [https://help.ubuntu.com/community/Gr...ing%20GRUB%202](https://help.ubuntu.com/community/Gr...ing%20GRUB%202)

Hopefully, the 1st thread will get you running, if not - the 2nd one certainly will
(Speaks from personal experience --> [http://www.vpolink.com/blog.php?b=2](http://www.vpolink.com/blog.php?b=2) Go have a giggle)

Hariks0.

---

