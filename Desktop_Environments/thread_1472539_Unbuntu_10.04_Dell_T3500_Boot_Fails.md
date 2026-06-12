---
title: "Unbuntu 10.04 Dell T3500 Boot Fails"
date: 2010-05-04
forum: Desktop Environments
---

### Post by arthursc on 2010-05-04
Hi 

Trying to install 64bit onto Dell T3500 with NVidia Quadro NVS 295.

Live Cd works and Install completes.

When I boot I get BIOS and Disk info then boot switches to flashing cursor after disk read and then Monitor goes into sleep mode. 

PC appears Not to continue booting. Any ideas?

Fedora installs and works fine...

Regards
ArthursC

---

### Post by arthursc on 2010-05-04
bump

---

### Post by tgalati4 on 2010-05-04
Try turning of the kernel-mode-setting KMS using the kernel boot switch.  You will have to boot into a rescue shell (root console) and make the appropriate change.  I don't have that switch handy but someone will shortly.

Alternatively, try in the root console:

dpkg-reconfigure -phigh xserver-xorg

reboot

---

### Post by arthursc on 2010-05-04
> **tgalati4 said:**
> Try turning of the kernel-mode-setting KMS using the kernel boot switch.  You will have to boot into a rescue shell (root console) and make the appropriate change.  I don't have that switch handy but someone will shortly.

Alternatively, try in the root console:

dpkg-reconfigure -phigh xserver-xorg

reboot

Thanks for the reply.

How can I get into the rescue shell as I do not even see any screen print at boot. I just get a flashing cursor for 10 seconds then the monitor goes into sleep.

Thanks

---

### Post by arthursc on 2010-05-05
I have managed to get to the point where I can boot into desktop gui with adding nomodeset.

I need to be able to get drop out of x to install nvidia drivers. Can anyone help here on this?

thanks.

---

### Post by Maarten74 on 2010-05-11
Hi

You've probably fixed it already, but I had the same problem on a Dell precision T5500 and this worked for me:

1. During startup, keep "SHIFT" pressed until you're in the grub menu
2. Once in the grub menu, press "e"
3. Find the line with "quiet splash" and type "nomodeset" after it
4. Press "CTRL+x" to boot
5. This started ubuntu for me (although with a subpar graphics driver"). I could then install the proprietary NVIDIA driver (why do you need to drop out of x?) and could reboot normally.

---

### Post by Adversus on 2010-09-08
> **Maarten74 said:**
> Hi

You've probably fixed it already, but I had the same problem on a Dell precision T5500 and this worked for me:

1. During startup, keep "SHIFT" pressed until you're in the grub menu
2. Once in the grub menu, press "e"
3. Find the line with "quiet splash" and type "nomodeset" after it
4. Press "CTRL+x" to boot
5. This started ubuntu for me (although with a subpar graphics driver"). I could then install the proprietary NVIDIA driver (why do you need to drop out of x?) and could reboot normally.

This fixed it for me, thanks!

---

