---
title: "Windows 7 wont boot after install"
date: 2009-05-23
forum: General Help
---

### Post by handlovitch on 2009-05-23
I tried installing ubuntu on my flash drive but now i cant boot into my normal OS without my flash drive being plugged into my computer. Once i boot into my normally OS i can remove it, but i cant resume hibernation without it plugged in. I can boot into ubuntu fine with my flash drive as well. My OS is windows 7 Evalution copy build 7100. How can I make it so I don't need my flash drive to boot to my normal OS?
 
Thanks for any help

---

### Post by hyperdude111 on 2009-05-23
You installed the bootloader to the flash drive, meaning the flash drive contains grub. You should have disconnected the hard drive before install. 

To fix enable the windows bootloader that comes with 7 (while the usb is unplugged) then use the bios to chose where to boot from.

---

