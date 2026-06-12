---
title: "Out of range tty console problem in Jaunty (How do I disable vesafb?)"
date: 2009-06-04
forum: General Help
---

### Post by atyndall on 2009-06-04
Hello,

I recently tried to set my tty (console windows, you get to them by pressing Ctrl+Alt+F1-F6) to a resolution of 1280x1024. I received out of range errors on my monitor, and then tried enabling 'sisfb' (the SiS framebuffer), following the instructions at [http://ubuntuforums.org/showthread.php?t=585454](http://ubuntuforums.org/showthread.php?t=585454).

My problem is, that I can enable sisfb (I place it in /etc/initramfs-tools/modules along with 'fbcon'), but for some inexplicable reason, vesafb will not allow itself to be blacklisted via /etc/modprobe.d/blacklist-framebuffer.conf and when I start up my computer, both framebuffers start up, and the SiS framebuffer promptly shuts down because vesafb has already taken control of the framebuffer functions.
```
$ dmesg | grep "fb"
[    0.677214] PCI: PCI BIOS revision 2.10 entry at 0xfb5a0, last bus=1
[    0.742914] system 00:00: iomem range 0xf8000-0xfbfff could not be reserved
[    4.083528] vesafb: framebuffer at 0xd8000000, mapped to 0xf7d00000, using 10240k, total 16384k
[    4.083547] vesafb: mode is 1280x1024x32, linelength=5120, pages=0
[    4.083554] vesafb: protected mode interface info at c6fd:000c
[    4.083561] vesafb: pmi: set display start = c00c7006, set palette = c00c704a
[    4.083567] vesafb: scrolling: redraw
[    4.083572] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    4.335533] fb0: VESA VGA frame buffer device
[    4.726568] sisfb: Video ROM found
[    4.727583] sisfb: Fatal error: Unable to reserve 32MB framebuffer memory
[    4.729534] sisfb: Is there another framebuffer driver active?

```

I tried the fixes outlined in [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/87158](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/87158), but disabling usplash and adding -b to the modprobes within that file (and various combinations of those) do not success in disabling vesafb.

My current GRUB boot line is as follows:
```
/boot/vmlinuz-2.6.28-11-generic root=UUID=17d32dd3-6a2c-4922-92b2-ff1249f324cf ro vga=795
```I am running Xubuntu 9.04 Jaunty (although I don't think the xubuntu part matters). Can anyone explain to me either how to finally disable vesafb, or how to fix the out of range high-res terminal problem?

Thanks in advanced.

---

### Post by agent8131 on 2011-04-24
I just got around to fixing this on one of my systems where it's been a longstanding problem.  I removed the vga= line from /boot/grub/menu.lst.  And I added a blacklist radeon and blacklist vesafb to /etc/modprobe.d/blacklist.conf.  Then I ran update-initramfs -k all -u

---

