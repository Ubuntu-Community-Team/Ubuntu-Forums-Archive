---
title: "how do I change menu.lst"
date: 2009-04-11
forum: General Help
---

### Post by kaykav on 2009-04-11
Good morning,
                   I just upgraded from 8.04 (hardy heron) to 8.10 (ibex).
             I think I didn't allow a change to the menu.lst. It still indicates 'Ubuntu 8.04'. The operation is 'Ibex' but the menu says 'Hardy'. I would like to change it without a problem. Thank you...Rich

---

### Post by Domas on 2009-04-11
gksudo gedit /boot/grub/menu.lst

## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=1b9ca8f0-c54c-4758-9545-cfb20849e204 ro quiet splash
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windoze
root		(hd0,0)
savedefault
makeactive
chainloader	+1

Change title Ubuntu 8.04, kernel 2.6.24-16-generic to title Ibex 8.10. Cheers

---

### Post by kaykav on 2009-04-14
Thanks for the info. I just wanted to make sure I wouldn't screw up.
                                           Rich

---

