---
title: "Boot Up Logo Issue"
date: 2009-01-18
forum: General Help
---

### Post by Tom_T on 2009-01-18
Hi

I've got Ubuntu installed as a dual boot with Linpus Linux on an Acer One NetBook.

All this works very well and I'm happy with the configuration of things... BUT !!

Since I added an image to the Grub back ground the Ubuntu Logo is now grey scale and off centre. Ubuntu loads fine, it just doesn't look right whilst it loads.

The Grub boot back ground is 640 x 480 14 colours and was set using Start Up Manager.

Any Ideas ?

Thanks :)

---

### Post by caljohnsmith on 2009-01-18
Sounds like a really strange problem, but I think I would check your menu.lst to see if there are any funny options at the end of the "kernel" line for your Ubuntu entries. That's a long shot, but it would at least be worth checking to make sure it isn't the problem. If you want, you could post your menu.lst if you would like some help checking it:
```
cat /boot/grub/menu.lst
```

---

