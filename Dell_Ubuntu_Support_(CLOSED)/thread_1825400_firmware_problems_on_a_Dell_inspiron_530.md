---
title: "firmware problems on a Dell inspiron 530"
date: 2011-08-15
forum: Dell Ubuntu Support (CLOSED)
---

### Post by LinuxSavedMyComputer on 2011-08-15
After i installed 32-bit ubuntu onto my computer(I later realized that my processor was 64-bit even though i had 32-bit vista.) I noticed 2 problems, the unity interface would not load and it loaded to gnome 2.x, also some WiFi firmware was missing so i could not acess the internet. I reinstalled it making sure to check the install 3rd party software

I have a few questions, 
1. Why can't i install 32-bit ubuntu with wifi and unity (apparently i have broadcom 802.11g network adapter and a nvidia graphics card but i don't know which one)
2. should i install 64-bit ubuntu if i only have 2gb of ram
3.I noticed three ubuntu partitions 1 of 35gb and 2 of 2g. Is this normal (i set ubuntu to use 40gb).

I can't use ubuntu unless it has wifi

I am not using wubi, i am dual-booting

---

### Post by TBABill on 2011-08-15
You probably have a video card that requires a proprietary (ATi or nVidia) driver so once you install that driver post-installation, then you should be able to get to Unity. It defaults back to standard Gnome when the system cannot handle 3D in its present configuration...that's normal.
 
The firmware you require is not automatically installed. If it's a Dell there's a likelihood it's a Broadcom chipset and you can usually get it installed by going to Additional Drivers and following the steps from the GUI.
 
You don't need 64 bit and with 2 GB RAM I don't know if you'd notice a difference. I always run 64 bit, but my RAM is higher. You're perfectly fine running 32 bit but you can try 64 bit and see if it improves performance in any way. No harm either way.
 
The extra 2GB partition is probably caused by the installer since you installed twice. It may have made an extra swap partition, but I can't say for certain that's what happened.

---

### Post by LinuxSavedMyComputer on 2011-08-15
It shows that there are no drivers installed and that none are available. I check, install 3rd party drivers

---

