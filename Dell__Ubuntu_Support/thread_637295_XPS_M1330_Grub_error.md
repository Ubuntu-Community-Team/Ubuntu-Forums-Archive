---
title: "XPS M1330 Grub error"
date: 2007-12-10
forum: Dell  Ubuntu Support
---

### Post by voodoo_child on 2007-12-10
Hi, 
I've installed ubuntu 7.10 live CD to an external USB hard-drive to use with my XPSM1330.

It was my first linux install, but i got everything working fine in the end, and im delighted with the results. When i have the guts, i'll probably install Ubuntu to the internal HD, but because I don't know anything about partitions, i decided to play it safe and use the external drive for Ubuntu.

The only problem i have now is that when i want to boot into Vista as normal, I need to have the USB drive connected or else the grub application fails. 

If i connect the USB drive before turning it on, it's fine, grub loads and i can select Vista and boot perfectly. But I want to have it so that if the USB drive isnt connected, Vista starts up as normal. 

Is this possible?

Thanks

---

### Post by MikkelTr on 2007-12-11
I have the exact same problem, although im using XP instead of Vista but dont think that matters. Grub just fails to load unless the external drive is connected.

---

### Post by voodoo_child on 2007-12-11
> **MikkelTr said:**
> I have the exact same problem, although im using XP instead of Vista but dont think that matters. Grub just fails to load unless the external drive is connected.

Yes that is exactly the problem I am having. Grub loads up, and when it is unable to find the external hard-drive, it just hangs. 

I think what i need to do is restore the master boot record for vista, and just forget about ubuntu. I'll let you know how I get on (not really sure what i'm doing:(), but i think my solution will be different to yours, as I think the method for restoring the MBR is different for XP and vista.

Googling for Grub error 21 does turn up a lot of hits, but as usual, separating the good advice from the bad is difficult.

---

### Post by MikkelTr on 2007-12-11
I take it that your internal disk is also a SATA?
Im pretty sure the problem lies in that when grub loads the menu.lst, it cant find the partition as stated in the file. Im my case the menu.lst looks like this 

```

title           Ubuntu 7.10, kernel 2.6.22-14-generic
root            (hd1,0)
kernel          /boot/vmlinuz-2.6.22-14-generic root=UUID=2c496d68-c5f8-4518-be4d-36e9f793085e
initrd          /boot/initrd.img-2.6.22-14-generic

```

I am having my real first go at linux as we are speaking, but I am pretty certain its the (hd1.0) line thats causing the error. Think im gonna check out other boot loaders, Supergrub from a cdrom first, and see how it goes.

---

### Post by voodoo_child on 2007-12-11
Im not sure if  my hard-drive is SATA tbh.

I ran my vista install disc and  restored the original Windows MBR, and Vista now loads as normal. I can't boot Ubuntu now obviously, but that's a problem for another day :)

---

