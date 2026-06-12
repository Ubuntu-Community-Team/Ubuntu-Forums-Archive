---
title: "Dell xps m1530 mouse problem"
date: 2009-01-04
forum: Dell Ubuntu Support (CLOSED)
---

### Post by pookito on 2009-01-04
Guys, I just upgraded to ubuntu 8.10 and my mouse pad is not working.  Any idea why?  I do have a separate partition for Sabayon Linux and the mouse pad is working perfectly, I do not understand why is not working fine under Ubuntu 8.10.  Any ideas on how to fix it.


Thanks.

pookito

---

### Post by spongypants23 on 2009-01-04
I'm going to assume you mean the touchpad?

You probably need to edit the boot line to include:
```
i8042.nomux=1
```

To do this, Press Alt+F2, and run
```
gksudo gedit /boot/grub/menu.lst
```

and make sure that the portion with the boot options looks like this:

```
title		Ubuntu 8.04.1, kernel 2.6.24-22-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-22-generic root=UUID=cd3f92b5-da71-49c8-8cf8-61d78e2bc2f6 ro quiet **i8042.nomux=1** splash
initrd		/boot/initrd.img-2.6.24-22-generic
```

Your version and kernel version are probably different, but the important thing is the presence of the i8042.nomux=1.

Do that and reboot, and it should work.

---

### Post by ussndmac on 2009-01-05
Interesting.

I have a different problem with the touchpad on my 1530.

It appears to be disabled, but, if while typing, I accidentally touch the scroll bar area of the touchpad it starts sending keystrokes.

Apparently some of the keys sent are F7, and lots of them, which causes a popup to display in Firefox wanting to know if I want Caret Browsing activated. This happens for every F7!

If it happens in a terminal window, lots of tildy's show up.

Is there a fix for this?

Regards,
Mac

---

### Post by spongypants23 on 2009-01-05
> **ussndmac said:**
> Interesting.

I have a different problem with the touchpad on my 1530.

It appears to be disabled, but, if while typing, I accidentally touch the scroll bar area of the touchpad it starts sending keystrokes.

Apparently some of the keys sent are F7, and lots of them, which causes a popup to display in Firefox wanting to know if I want Caret Browsing activated. This happens for every F7!

If it happens in a terminal window, lots of tildy's show up.

Is there a fix for this?

Regards,
Mac

Yeah. When i first installed Ubuntu on my laptop, I had this problem as well. Try the steps in my post above, it should fix it.

---

### Post by pookito on 2009-01-05
Dude, thank you so much.  It fixed the problem real quick.  Thanks for your quick replay.

pookito

---

