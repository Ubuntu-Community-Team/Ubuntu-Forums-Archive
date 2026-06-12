---
title: "intel video driver white screen"
date: 2010-02-15
forum: Desktop Environments
---

### Post by BigCdaAnswer3 on 2010-02-15
Hey all, I have a Intel Atom N270 CPU running Ubuntu Karmic. I have a VGA Monitor connected which the xorg intel driver successfully outputs to. I have a secondary LVDS monitor, which, at sometime during the boot sequence slowly fades to be a completely white screen (it shows up properly during BIOS init).

Has anyone seen any "white screen" issues with LVDS monitors in Karmic? Maybe the intel driver just can't drive two displays? I've had this problem before, which I believe I rectified by setting vga=791 in the grub configuration. However, I took the "quiet" and "splash" options out of grub, which works ok for a couple seconds, but then still slowly fades to white :(

---

