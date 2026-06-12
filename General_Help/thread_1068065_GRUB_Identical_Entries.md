---
title: "GRUB Identical Entries?"
date: 2009-02-12
forum: General Help
---

### Post by dremits on 2009-02-12
Hi,

There seems to be two identical entries in the Grub. Can I remove the identical lines? Are there any reprecautions if I do this?

Here is a copy of the list:

```
title		Ubuntu 8.10, kernel 2.6.27-11-generic
uuid		4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-11-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-11-generic (recovery mode)
uuid		4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50
kernel		/boot/vmlinuz-2.6.27-11-generic root=UUID=4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50 ro  single
initrd		/boot/initrd.img-2.6.27-11-generic

title		Ubuntu 8.10, kernel 2.6.27-7-generic
uuid		4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50 ro quiet splash 
initrd		/boot/initrd.img-2.6.27-7-generic
quiet

title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)
uuid		4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50
kernel		/boot/vmlinuz-2.6.27-7-generic root=UUID=4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50 ro  single
initrd		/boot/initrd.img-2.6.27-7-generic

title		Ubuntu 8.10, memtest86+
uuid		4dcfb4ea-59a8-4603-a6cc-7c9f5faf4f50
kernel		/boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST
```

Thanks.

---

### Post by Elfy on 2009-02-12
Not quite identical
title		Ubuntu 8.10, kernel [COLOR="Red"]2.6.27-11-generic[/COLOR]
title		Ubuntu 8.10, kernel 2.6.27-11-generic [COLOR="Red"](recovery mode)[/COLOR]
title		Ubuntu 8.10, kernel [COLOR="Red"]2.6.27-7-generic[/COLOR]
title		Ubuntu 8.10, kernel 2.6.27-7-generic (recovery mode)

Different kernels with their recovery partitions,a s you get kernel updates so thelist will get longer - I keep 2 sets - current and previous and periodically remove the older ones. Search in synaptic for linux-image - select older ones for complete removal.

---

### Post by dremits on 2009-02-12
Thanks for the reply. So do you think I should remove the .7 linux image?

---

### Post by Elfy on 2009-02-12
I like to keep a backup kernel personally - all it does is take a fairly small amount of room - but if you get rid of it and then a problem occurs with the newest kernel then you won't be able to boot if you have removed the previous one.

But obviously the choice is yours :)

You can change how many kernels grub keeps mine is set to keep all - you could change it to 2 - so that as new kernels are added - the last is removed

The part of the file you need to edit looks like

> ## e.g. howmany=all
##      howmany=7
# howmany=[COLOR="Red"]all[/COLOR]

Change all to 2 for example

To backup the file and then edit it

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.1202
gksudo gedit /boot/grub/menu.lst
```

---

### Post by dremits on 2009-02-12
I think i'll keep it then. I was mostly concerned I had to operating systems taking up unnessecary space but if the linux image is quite small then I'll keep it. I think when I get a newer one I will delete the oldest so I always have two but no more. 

Thanks very much.

---

### Post by Vico Vicario on 2009-02-12
If you edit menu.lst you will not remove the old kernels, but just hide them. If you want to remove old kernels use synaptic to look for linux-* packages and remove the older ones. But it is a good practice to keep at least 2 kernels for a few days after upgrading.

V

---

### Post by dremits on 2009-02-13
Thanks for clarifying. I will keep it for now but if I get any more I will delete the oldest one.

---

### Post by dremits on 2009-02-21
Is it ok to comment these out in the Grub list?

---

### Post by Kevbert on 2009-02-21
You can comment them out with a #, but personally I'd leave them as they are (if you have a problem you can boot into the older kernel to hopefully fix the new one).

---

### Post by dremits on 2009-02-22
Ok then. Thanks.

---

