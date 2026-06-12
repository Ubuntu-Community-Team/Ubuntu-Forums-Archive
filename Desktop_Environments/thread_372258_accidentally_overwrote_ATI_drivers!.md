---
title: "accidentally overwrote ATI drivers!"
date: 2007-02-28
forum: Desktop Environments
---

### Post by DMAthlon on 2007-02-28
i was installing beryl and my stupid self over wrote th ATI drivers with the nvidia ones and now i cant get into ubuntu. the message it gives me mentions Xorg. can any one offer me help? i dont want to have to reinstall :-/.

---

### Post by magicfab on 2007-02-28
When booting, hit ESC to get to the Grub menu. Choose the recovery boot mode. 

Once at the prompt, enter the following command;
dpkg-reconfigure xserver-xorg

the the following command:
reboot

That will reconfigure Xorg, then reboot. Come back and let us know how it went.

---

### Post by DMAthlon on 2007-02-28
i had to sudo the command and i went through a little process where it asks me questions about my monitor, graphics card, keyboard and mouse.

then i had to sudo reboot because i was root and that forced it to.

when i restarted, it still didnt work.

thanks for trying though.

---

### Post by DMAthlon on 2007-02-28
I'm back in ubuntu now thansk to this code:

```
sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r) #Okay if it is already installed
sudo apt-get install xorg-driver-fglrx
sudo depmod -a
sudo aticonfig --initial
sudo aticonfig --overlay-type=Xv
```

---

