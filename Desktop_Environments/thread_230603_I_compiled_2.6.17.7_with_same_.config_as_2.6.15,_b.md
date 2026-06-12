---
title: "I compiled 2.6.17.7 with same .config as 2.6.15, but it won't boot"
date: 2006-08-06
forum: Desktop Environments
---

### Post by kremso on 2006-08-06
Hi,

I tried to build a leightweight kernel(2.6.17.7 from kernel.org), so I only compiled things I need.
But my new kernel refused to boot with this weird message:
```

Uncompressing, OK booting
0 //this is zero

```

..and booting stops. In recovery mode, booting stops at Waiting for root file system...

So I tried to add some more drivers, because I thought I simply miss some IDE or chipset driver. Well, after one week and countless compilations I gave up.

I took the old .config and changed only these thigs:
[LIST]
[*]processor model
[*]unchecked keernel debugging
[*]unchecked support for >2TB disks and files and >4GB RAM
[*]unchecked all IO schedulers but CQF 
[/LIST]

But I'm left with the weird zero once again..

So what am I doing wrong. Isn't initrd the trouble? I was compiling it using make-kpkg --initrd, so it was created and has its entry in grub. I don't really know, what else could be causing this,

---

