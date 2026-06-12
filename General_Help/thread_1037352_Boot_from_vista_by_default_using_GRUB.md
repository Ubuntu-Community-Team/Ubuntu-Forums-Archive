---
title: "Boot from vista by default using GRUB"
date: 2009-01-11
forum: General Help
---

### Post by falconed7 on 2009-01-11
Hi everyone!

So I'm dual booting between Windows Vista and Ubuntu through GRUB.

I am looking for a way for the PC to automatically boot from Vista if the PC isnt touched for the 10 second count down. Is there a way to 'move' Vista up in priority when booting from the GRUB boot loader?

Cheers.

---

### Post by Zeroberry on 2009-01-11
Use the command

  sudo gedit /boot/grub/menu.lst

And manually move the Vista part up over the Ubuntu ones. Make sure you get all the lines in the right places.

---

### Post by falconed7 on 2009-01-11
> **Zeroberry said:**
> Use the command

  sudo gedit /boot/grub/menu.lst

And manually move the Vista part up over the Ubuntu ones. Make sure you get all the lines in the right places.

Okay thanks I'll give that a go now.

---

### Post by falconed7 on 2009-01-11
Okay I installed all of the new updates, restarted and now notice that there are 5 boot options related to ubuntu.

From /boot/grub/menu.lst:
```
## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		8c57c167-483e-439d-8580-b0f8b643193b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8c57c167-483e-439d-8580-b0f8b643193b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		8c57c167-483e-439d-8580-b0f8b643193b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8c57c167-483e-439d-8580-b0f8b643193b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		8c57c167-483e-439d-8580-b0f8b643193b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c57c167-483e-439d-8580-b0f8b643193b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		8c57c167-483e-439d-8580-b0f8b643193b
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=8c57c167-483e-439d-8580-b0f8b643193b ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		8c57c167-483e-439d-8580-b0f8b643193b
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```

So the updates have updated to a newer kernel? Am I safe to remove these from /boot/grub/menu.lst? ie. remove the last 3 options?

```

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title		Windows Vista/Longhorn (loader)
root		(hd0,0)
savedefault
makeactive
chainloader	+1

## ## End Default Options ##

title		Ubuntu 8.10, kernel 2.6.27-9-generic
uuid		8c57c167-483e-439d-8580-b0f8b643193b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8c57c167-483e-439d-8580-b0f8b643193b ro quiet splash 
initrd		/boot/initrd.img-2.6.27-9-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-9-generic (recovery mode)
uuid		8c57c167-483e-439d-8580-b0f8b643193b
kernel		/boot/vmlinuz-2.6.27-9-generic root=UUID=8c57c167-483e-439d-8580-b0f8b643193b ro  single
initrd		/boot/initrd.img-2.6.27-9-generic

### END DEBIAN AUTOMAGIC KERNELS LIST
```


Would it be okay to edit it like the above?

---

### Post by jonlemur on 2009-01-11
Yes, I've done that before and it just won't show the options to boot to the older kernels.  You might want to keep the part with the memtest, but that's up to you.

---

