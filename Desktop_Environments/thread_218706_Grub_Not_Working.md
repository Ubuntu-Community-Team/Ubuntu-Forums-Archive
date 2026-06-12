---
title: "Grub Not Working"
date: 2006-07-18
forum: Desktop Environments
---

### Post by fatalfurry on 2006-07-18
I just did some updates that required me to reboot my system and now it will not load grub. It gives the message

 GNU GRUB  version 0.96  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB lists possible command completions.  Anywhere else TAB lists the possible completions of a device/filename. ]

grub>

I have found a fix for gentoo here http://gentoo-wiki.com/HOWTO_Fix_Grub_it_can't_find_a_kernel
but it didnt work how do I fix this issue.

Thanks

---

### Post by OpsVentus on 2006-07-19
What commands did you try exactly?

If you got Ubuntu on your first drive on the first partition. You should go:
root (hd0,0)/boot
setup (hd0)
quit

First disk, second partition:
root (hd0,1)/boot
setup (hd0)
quit

Second disk, first partition:
root (hd1,0)/boot
setup (hd0)
quit

Does any of those work?

Cheers,
Bart.

---

### Post by fatalfurry on 2006-07-19
I tried all of those and the
root (hd0,0)/boot
setup (hd0)
quit

one went through and it looked like it found where grub was and it loaded the menu.list but when I restart it goes back to the 
grub> 
screen.

---

### Post by OpsVentus on 2006-07-19
You can try to boot the system by hand and then edit the menu.lst by hand.

Boot the system by hand:
When you get to 'grub>'
Type these commands:
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

This are the command's for the kernel I currently got. You may need to adjust these lines to your kernel.
So if these commands don't work, tell me what grub says when trying:
root (hd0,0)/boot
setup (hd0)
quit

Or the other one that did work(somewhat)

Edit the menu.lst by hand:
In terminal go:
#sudo gedit /boot/grub/menu.lst
The you get your menu.lst, there are all the boot entry's of grub stored.

Then add these lines:
title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

You may need to adjust these lines to your kernel like the boot command's.

Did you understand this? Else I can try to rewrite more clearly. And if you can figure out what your kernel is I can adjust the command's for you.
Cheers,
Bart.

---

### Post by fatalfurry on 2006-07-23
> root (hd0,1)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

I have been using root(hd0,0) but everything else is the same.
When I did that it did not like the savedefault command but it still booted into just the command line no gui. Then it says that it could not read /ect/fstab and some other folders. Then I tried to edit menu.lst by the #sudo gedit /boot/grub/menu.lst it did nothing. What can i do?

---

### Post by OpsVentus on 2006-07-24
If your Ubuntu is on the first disk first partition, then try this:
**root (hd0,0)**
**kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash**
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

Does that work?

Cheers,
Bart.

---

### Post by ex00r on 2006-07-24
> **OpsVentus said:**
> If your Ubuntu is on the first disk first partition, then try this:
**root (hd0,0)**
**kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash**
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

Does that work?

Cheers,
Bart.

I have exactely te same problem!

I did OpsVentus suggestion just with adaption to my system and it worked. I could finally log into my system again.

my menu.lst btw:

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd1,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdb1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

but in a LTS stabel version like dapper should something like this not happen!

---

### Post by OpsVentus on 2006-07-24
Yes it's a small problem, but with big consequenses.
Fortunally for you, it's Linux, we can fix it!

Cheers,
Bart.

---

### Post by fatalfurry on 2006-07-24
I got it!
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

but if I put that into the menu.lst it does the same thing forcing me to type it all in again.

---

### Post by OpsVentus on 2006-07-25
How does your menu.lst look now?

---

### Post by fatalfurry on 2006-07-25
it looked like this when I was done
title Ubuntu, kernel 2.6.15-26-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.15-26-386
savedefault
boot

but now it will not let me boot like it did last night. After I put in the kernel command it says like error 18: selected cylinder exceeds max supported by BIOS

---

### Post by OpsVentus on 2006-07-25
If you can boot to Ubuntu, try to reinstall your kernel.
This will put the kernel in the right place and reconfigure grub.

Cheers,
Bart.

---

