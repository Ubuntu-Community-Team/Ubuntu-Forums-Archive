---
title: "new installation"
date: 2006-10-07
forum: Desktop Environments
---

### Post by oger on 2006-10-07
hi i recently installed ubuntu on my laptop and liked it so have just installed it on my desktop. the problem is that now when the os selection screen comes up i am unable to toggle between the different systems because at this point the up/down arrows on my wireless keyboard do not work. any help would be much appreciated

---

### Post by pay on 2006-10-07
Make sure the keyboard is selected properly in /etc/X11/xorg.conf (should be difficult without a keyboard). If it is setup properly then maybe a newer kernel has the drivers for your keyboard.

---

### Post by rogier.de.groot on 2006-10-07
Make the BIOS recognize the keyboard - if it doesn't it won't work with GRUB which relies on the BIOS for things like that... How to do that depends on your BIOS - maybe enable USB keyboard support or somesuch...

---

### Post by oger on 2006-10-07
thanks for the help i had to enable usb keyboard in bios. all working fine now

---

