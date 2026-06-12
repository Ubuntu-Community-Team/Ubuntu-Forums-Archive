---
title: "Weird Issue with Nvidia drivers"
date: 2006-06-18
forum: Desktop Environments
---

### Post by lt paul on 2006-06-18
I'm experinceing a strange problem with the Nvidia drivers. I have a GeForce2 and a TNT2 card in my system. After installing the Nvidia drivers the TNT2 card worked and was used once x started but the GeForce was used during boot but didn't work once X started. I have attached my xorg.conf and x log. I changed the Nvidia entry on the geforce 2  to NV so it works for now, but I would like to get 3d acceleration working.

---

### Post by tseliot on 2006-06-18
[QUOTE=lt paul]I'm experinceing a strange problem with the Nvidia drivers. I have a GeForce2 and a TNT2 card in my system. After installing the Nvidia drivers the TNT2 card worked and was used once x started but the GeForce was used during boot but didn't work once X started. I have attached my xorg.conf and x log. I changed the Nvidia entry on the geforce 2  to NV so it works for now, but I would like to get 3d acceleration working.[/QUOTE]
Try adding the following options to the Section device (of your xorg.conf) of each of your cards:
```
Option "RenderAccel" "True"
Option "AllowGLXWithComposite" "on"
```

---

### Post by lt paul on 2006-06-18
No luck, same error. I had this card working with the Nvidia Driver and [this]("http://www.ubuntuforums.org/showthread.php?t=159925") xorg.conf before. I have made a few system changes since then ( the main one being that I moved the cards around) but I would think that the Device settings should still work, still no dice.

---

### Post by FredB on 2006-06-19
Which driver are you using : for nvidia cards before GeForce 3, you will have to use Nvidia legacy package.

---

### Post by lt paul on 2006-06-19
I'm using the legacy drivers. If I pull the TNT2 from the system physically I can get the GF2 to work, but adding the TNT2 in any slot, even with all the xorg.conf entries commented keeps x from starting.  

I get this error
```

(--) NVIDIA(0): Linear framebuffer at 0x88000000
(--) NVIDIA(0): MMIO registers at 0x80000000
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

```

---

### Post by tseliot on 2006-06-20
[QUOTE=lt paul]I'm using the legacy drivers. If I pull the TNT2 from the system physically I can get the GF2 to work, but adding the TNT2 in any slot, even with all the xorg.conf entries commented keeps x from starting.  

I get this error
```

(--) NVIDIA(0): Linear framebuffer at 0x88000000
(--) NVIDIA(0): MMIO registers at 0x80000000
(EE) NVIDIA(0): Failed to initialize the NVIDIA graphics device!
(EE) NVIDIA(0):  *** Aborting ***
(II) UnloadModule: "nvidia"
(EE) Screen(s) found, but none have a usable configuration.

```[/QUOTE]
Plug in the card
Boot in Recovery Mode (select it from the Grub menu almost as soon as you turn on your computer).
then type:
```
dpkg-reconfigure xserver-xorg

```
and select your card and driver

Then restart your computer by typing:
```
reboot
```

---

