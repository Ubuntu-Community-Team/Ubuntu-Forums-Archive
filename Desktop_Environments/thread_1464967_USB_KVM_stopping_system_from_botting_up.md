---
title: "USB KVM stopping system from botting up"
date: 2010-04-28
forum: Desktop Environments
---

### Post by jazee on 2010-04-28
When ever I have my Keyboard (USB non wireless) plugged into the USB KVM. My system fails to boot up. It gets past the Grub loader at which point I am able to navigate Grub using the keyboard. Shortly after pressing ender on the Grub entry. I hit a black screen at which it stalls out. This is before the White Ubuntu logo appears. Any ideas of what might be the problem?

---

### Post by greenslime on 2010-04-29
Sounds like the same problem I am having... [http://ubuntuforums.org/showthread.php?t=1454211]("http://ubuntuforums.org/showthread.php?t=1454211")

No luck yet.  I'm pretty sure it's something with Karmic, not the switch itself, since I actually went out and bought a different type of usb dvi kvm switch and got exactly the same result.  :(

---

### Post by greenslime on 2010-04-29
Heh... after posting the above I got frustrated and found a solution.

Adding "pci=noacpi" to the kernel boot parameters allowed me to boot without disconnecting the usb kvm.

The steps for doing this with GRUB2 are a bit convoluted, so I recommend trying it by editing the boot options during boot (esc to get grub menu during boot, e to edit, go to the end of the last line and add "pci=noacpi" (no quotes), then ctrl-x to boot).  If that works, refer to the GRUB2 online docs for making it permenent.

---

