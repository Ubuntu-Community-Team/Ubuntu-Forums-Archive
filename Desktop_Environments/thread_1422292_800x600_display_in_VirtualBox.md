---
title: "800x600 display in VirtualBox"
date: 2010-03-05
forum: Desktop Environments
---

### Post by dragos2 on 2010-03-05
I don't know if its the correct section.

I am running some Ubuntu Desktops in VirtualBox, but all of them have a resolution
of 800x600 and I can't set them higher.

As host I am running Win 7 Ultimate 64, and as guest Ubuntu Desktop 9.10 64 bits with
1 GB of RAM allocated to the virtual machine.

My display monitor is a 22" Benq G2200W.

What drivers do I need to install or what setting do I have to change ?

---

### Post by squaregoldfish on 2010-03-05
Have you installed the VirtualBox Guest Additions? (There should be a menu entry for it at the top of the VM window.)

Steve.

---

### Post by dragos2 on 2010-03-05
> **squaregoldfish said:**
> Have you installed the VirtualBox Guest Additions? (There should be a menu entry for it at the top of the VM window.)

Steve.

This way I have higher resolution, thanks.

It does not detect all resolutions but better than before.

Thanks

---

### Post by squaregoldfish on 2010-03-05
Now you have this installed, you should be able to resize the VM's window to whatever size you like, and the Windows desktop will follow suit. There should also be an option to run full screen. Essentially, you can ignore the desktop settings in Windows completely.

Steve.

---

