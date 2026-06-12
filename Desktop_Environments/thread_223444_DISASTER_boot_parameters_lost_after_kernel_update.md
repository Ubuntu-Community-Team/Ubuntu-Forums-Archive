---
title: "DISASTER: boot parameters lost after kernel update"
date: 2006-07-26
forum: Desktop Environments
---

### Post by SqRt7744 on 2006-07-26
Hello,

I've installed Ubuntu on my cousin's computer and he likes it, unfortunately every time there is a kernel update the menu.lst file is rewritten.  This is really bad, because for linux to work properly on his computer it must boot with the parameters pci=noapic and noacpi. (otherwise no net, USB craps out, mouse gets jerky etc)

Is there anyway to have these parameters NOT be deleted from the boot line for the previous kernel and/or automatically added to the boot line for the new kernel in /boot/grub/menu.lst?

He is not very tech savvy, and unfortunately I will be leaving the country for a long time and won't be able to manually edit the file for him.

---

### Post by Irony on 2006-07-26
Can those options be put outside the END DEBIAN AUTOMAGIC KERNELS LIST then they won't be updated.

---

### Post by az on 2006-07-26
add
pci=noapic, noacpi
to the line: "# kopt=root=/dev/hda3 ro" in /boot/grub/menu.lst
Like this:


## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro 
# kopt=root=/dev/hda3 ro pci=noapic, noacpi



Yes, the line is commented, but every time update-grub is run, those default options will be added to each stanza.

Run 
sudo update-grub

and you are good to go.

---

### Post by SqRt7744 on 2006-07-26
Thanks so much for the replies.  Typical me though... if I'd actually read the header in the menu.lst file, I would have been able to figure this out by myself  :oops:

---

