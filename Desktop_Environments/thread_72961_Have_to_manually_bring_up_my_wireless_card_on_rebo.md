---
title: "Have to manually bring up my wireless card on reboot...how to automate?"
date: 2005-10-07
forum: Desktop Environments
---

### Post by dougr on 2005-10-07
Hi,

Everytime I reboot my computer, I need to go to the location that I have my wireless card driver, and then type

sudo insmod rt2500.ko

Then I am able to activate my wireless card, and all works fine.  Is there a way that I can automate this process?  I followed the instructions for setting up this card in the wiki originally, but it did not give me a method to automate it.

Thanks

---

### Post by Alexander Kirillov on 2005-10-07
[QUOTE=dougr]Hi,

Everytime I reboot my computer, I need to go to the location that I have my wireless card driver, and then type

sudo insmod rt2500.ko

Then I am able to activate my wireless card, and all works fine.  Is there a way that I can automate this process?  I followed the instructions for setting up this card in the wiki originally, but it did not give me a method to automate it.

Thanks[/QUOTE]
Add module name to /etc/modules

---

### Post by nuk130n on 2005-10-07
[QUOTE=Alexander Kirillov]Add module name to /etc/modules[/QUOTE]

I'm quite sure that won't work if he doesn't place the driver somewhere modprobe and friends can find it.

Have you tried doing a make install after make ?

If that fails you could copy the *.ko file to /lib/modules/`uname -r`/kernel/drivers/net/wireless/

Iirc it should be automagically found during the next reboot.

Good luck!

---

### Post by dougr on 2005-10-07
[QUOTE=nuk130n]I'm quite sure that won't work if he doesn't place the driver somewhere modprobe and friends can find it.

Have you tried doing a make install after make ?

If that fails you could copy the *.ko file to /lib/modules/`uname -r`/kernel/drivers/net/wireless/

Iirc it should be automagically found during the next reboot.

Good luck![/QUOTE]

worked perfectly...thanks a lot!

---

