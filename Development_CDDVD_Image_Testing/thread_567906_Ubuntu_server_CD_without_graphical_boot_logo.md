---
title: "Ubuntu server CD without graphical boot logo"
date: 2007-10-05
forum: Development CD/DVD Image Testing
---

### Post by tobler on 2007-10-05
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/83642](https://bugs.launchpad.net/ubuntu/+bug/83642) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hello

There seems to be a problem on Intel processor and Xen / KVM virtualization. Already bug reported [https://bugs.launchpad.net/ubuntu/+bug/83642](https://bugs.launchpad.net/ubuntu/+bug/83642) that server installation CD is not able to boot on virtualization environment because of isolinux graphical boot logo. It just hangs there so installation is not possible.
I hope you to notice this when you create new CD images for server.

Right now I need to create own server CD and modify isolinux.cfg not to have graphics. So then I can install Ubuntu server on virtualized environment.

---

### Post by tobler on 2007-10-05
For users who need to install Ubuntu into Intel virtualized machine, here is guide how to avoid installation cd boot hang.
1. Extract cdrom contents into isoimage/ folder
2. Edit isoimage/isolinux/isolinux.cfg configuration file and remove text "GFXBOOT bootlogo"
3. Change to isoimage/ directory and create new cdrom image file with command:
[indent]```
mkisofs -o ../ubuntu-7.10-beta-server-i386-2.iso -b isolinux/isolinux.bin -c isolinux/boot.cat -no-emul-boot -boot-load-size 4 -boot-info-table -l -R -r .
```[/indent]
4. Note that I used ...i386-2.iso filename. You may change that. Finally burn that image or use on Xen / KVM directly.

---

