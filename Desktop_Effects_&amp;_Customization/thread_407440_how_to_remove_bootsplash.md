---
title: "how to remove bootsplash"
date: 2007-04-12
forum: Desktop Effects &amp; Customization
---

### Post by graha on 2007-04-12
is there a way to remove bootsplash?

---

### Post by Rospo Zoppo on 2007-04-12
sudo update-alternatives --config usplash-artwork.so and select usplash-theme-ubuntu.so
then
sudo update-initramfs -u

---

### Post by FuturePilot on 2007-04-12
If you need to do it temporarily, at the grub menu highlight the kernel you need to boot (Don't press Enter) and press "e" then there should be 3 more lines that come up. Highlight the line that begins with "kernel" and press "e" again. Then use the arrow keys to go all the way to the end of that line and remove the words "quiet splash". Then press Enter. Then press Enter again to boot and the splash should be gone now. To make it permanent  ```
sudo gedit /boot/grub/menu.lst

```
Then find the latest kernel and remove "quiet splash" from the end of that line.

---

