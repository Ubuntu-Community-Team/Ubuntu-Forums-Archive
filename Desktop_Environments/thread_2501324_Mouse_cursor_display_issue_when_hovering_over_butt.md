---
title: "Mouse cursor display issue when hovering over button"
date: 2024-10-02
forum: Desktop Environments
---

### Post by pol2095 on 2024-10-02
Hello,


I have an application (GTK2) that when hovering over a button should display a hand, and when leaving the button the arrow should reappear like on a hyperlink, but the hand does not disappear on my x64 PC.
What is strange, on my Raspberry Pi 5 ARM64, the same application works normally.

This bug occur only on Wayland, not Xorg.

Is there a setting in Ubuntu to fix this problem?

I have the same problem using Fedora 40 and Wayland but not with Ubuntu 22.04.5 amd64, I think something has been changed in the Linux kernel or Gnome that causes this bug with some Intel graphics cards (for example Intel HD Graphics 620).

Thanks

---

### Post by pol2095 on 2024-10-13
A MUTTER bug has been reported [here]("https://gitlab.gnome.org/GNOME/mutter/-/issues/3735"), but Gnome support doesn't seem very responsive.

---

