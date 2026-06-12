---
title: "Booting Idea, and Question"
date: 2009-05-30
forum: General Help
---

### Post by istar9 on 2009-05-30
Not sure if this can be done, But wouldn't think it would be to hard. 

I have the latest Ubunutu on one drive and Windows on another. Was wondering If it would be doable to have the windows boot be default on the system. aka Turn comp on it goes to windows.. Though If have the files on a usb flash drive which when plugged in the comp will boot ubuntu ? 

Obviously the Files on the USB drive will only work for this specific comp, due to the hardware configurations, so it will just be for this comp. But interested if this could be done.

---

### Post by Ocxic on 2009-05-30
what you can do is edit the "/boot/grub/menu.lst" and set windows as your default startup.

```

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not use 'savedefault' or your
# array will desync and will not let you boot your system.
default         0

```Check the list of options when you start the computer, if you have 5 entries and windows is the third you would set "default 2" because the numbering starts at 0

---

### Post by pastalavista on 2009-05-30
When you set the BIOS to boot from USB first, CD second and HDD third, that is exactly how it works... if each drive has its own boot sector. If the USB drive is connected, it boots from that and if not it boots from the HDD, unless you have a bootable CD in the drive.

So if you want to install to a USB drive, make sure you also install grub to that drive and not the HDD (which is the default option). Then boot is controlled strictly by the BIOS setting and you won't lose the original HDD boot sector.

---

### Post by istar9 on 2009-05-31
Thank you for the replies they helped, have it all setup now ;)

---

