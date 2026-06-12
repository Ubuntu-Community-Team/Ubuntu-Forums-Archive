---
title: "screen saver freezes my computer"
date: 2009-06-01
forum: General Help
---

### Post by gaffajoiner on 2009-06-01
Installed the latest ubuntu version no problems with it, it is when i set a screen saver it worked well, but now which ever screen saver i chose the computer freezes i have to take the battery out of my laptop and reboot,

---

### Post by pastalavista on 2009-06-01
The latest release (9.04) has changed it's inter-operability with graphics drivers which is probably why you're having trouble with the screensaver. Either use a less graphics intensive one (I use the pictures slideshow) or else try booting to the previous kernel version and see if the problem remains.

Also to safely restart the computer without having to remove the battery, press these keys in this order.. while holding ALt+PrintScreen press R,S,E,I,N,U,B

---

### Post by gaffajoiner on 2009-06-01
Thanks for the info, please can you tell me how to boot to the previous kernel version

---

### Post by Soul-Sing on 2009-06-01
> Either use a less graphics intensive one (I use the pictures slideshow

+1
for instance black.

---

### Post by pastalavista on 2009-06-01
> **gaffajoiner said:**
> Thanks for the info, please can you tell me how to boot to the previous kernel version
Sorry about that advice because if you just did a fresh install, you won't have any previous kernels. They would show on the grub (boot loader) menu. You may have to hit escape at the first load screen to see the grub menu and if you have any older kernels, they would appear below the newest one.

---

