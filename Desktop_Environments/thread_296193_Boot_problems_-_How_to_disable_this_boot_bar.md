---
title: "Boot problems - How to disable this boot bar"
date: 2006-11-09
forum: Desktop Environments
---

### Post by info99 on 2006-11-09
Hello!

I have problems booting my ubuntu 6.10 edgy. This is a updated version of 6.06 dapper. I updates just after the release of 6.10, but this booting problems occured just today.

I see the xubuntu booting bar (or how this is called) and it stops a little bit after the middle of the second section. The I cannot do anything but a reboot (just a hard reset is possible). 

I don't how what causes this problem. 

Is there any method do disable this nice looking bar and the image behind it and to see all the boot messages?

I tried to remove the quite and splash options in grub, but this did not help.

Thanks in advance.

---

### Post by Najand on 2006-11-09
Just boot with nosplash option:

When booting, when you see the grub menu(if not press "Esc" when grub starts, to see that), use 'e' botton to edit the grub command and change "splash" to "nosplash", click enter and continue to boot.

---

