---
title: "X won't start."
date: 2007-03-12
forum: Desktop Environments
---

### Post by metaru on 2007-03-12
I just installed kubuntu with beryl and it worked perfectly until I restarted my computer. I got an error saying that my x version and kernel version do not match, however I can start x if I reinstall the newest nvidia drivers but that only solves it until I restart my computer again. So I'm wondering if there's any solution to this??

---

### Post by pillu on 2007-03-23
Same problem here. I have intel GMA 945 instead of nVidea. I think the problem happened because I configured beryl to start automatically on startup. Did you do this too ? Or did this happen without that as well.

Any pointers on how to get my X server up and running without a full reinstall will be much appreciated.

pillu

---

### Post by errhec on 2007-03-23
Boot your computer up, on grub at the start choose the safe mode.
After is done type
sudo dpkg-reconfigure xserver-xorg

This will reconfigure your Xserver and you be able to go to xserver

after you reconfigure joust type 

xserver

this will start your GUI :)
Hope it helps

---

