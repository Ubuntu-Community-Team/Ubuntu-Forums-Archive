---
title: "Inspiron E1505n Issue!"
date: 2007-07-05
forum: Dell  Ubuntu Support
---

### Post by khunt2 on 2007-07-05
I recieved my new Inspiron E1505n with ubuntu pre-installed from Dell the other day.  I turned it on, and was notified that updates were available when my internet connection started working. When I restart the computer after updating, I get an error:

```
Error 17: Cannot mount selected partition

Press any key to continue...
```

Strange, because all I did with the factory-installed-linux PC was install the updates that Ubuntu advised me to.  Any ideas?

---

### Post by rfruth on 2007-07-05
GRUB problem (error 17) - did it come with factory restore disk(s) ?  If so & there is none of your data that might be easier ...

---

### Post by SaguratuS on 2007-07-06
I was rather surprised when I ran into this as well when I first picked up my 1505n.  On the early systems, dell made a bit of a typo in the grub configuration.

What you need to do is when the grub screen comes up, hit esc to get to the grub menu, then press e.
Select "root (hd0,0)", press e again, and change that to "root (hd0,2)"
Hit enter, press b to boot.  Once your system is up, you need to edit /boot/grub/menu.lst and change "# groot=(hd0,0)" to "# groot=(hd0,2)"
Save, then run update-grub

I assume that the partition layout will be the same for your system, however if this isn't the case, you'll need to change hd0,x to match your root partition


What happens: Initially, the partition entries in grub are correct, however the groot setting is incorrect (used with the debian update-grub tool for automatic grub kernel entry generation).  When you update your system, a newer kernel is installed, and update-grub is executed, changing the root to an incorrect value.

---

