---
title: "Fedora broke my Ubuntu"
date: 2006-05-22
forum: Desktop Environments
---

### Post by joehayhurst on 2006-05-22
Hello all

This is the first time I've had to post a request, it's a good one! Everyone seems very helpful, so here goes.

I installed Fedora Core 5 on another partition on my laptop. Unfortunately it seems to have ruined my Grub config. Fedora didn't seem to recognise my Ubuntu installation correctly, so when it had finished I could only boot into Fedora -- there was no option to boot Ubuntu on the menu. I have added the following lines to the bottom of the /etc/grub.conf file:

title Ubuntu (2.6.12-10-386)
        root (hd0,0)
        kernel /boot/vmlinuz-2.6.12-10-386 ro root=LABEL=/1 rhgb quiet
        initrd /boot/initrd.img-2.6.12-10-386

I can now see this installation in the Grub menu, and when I select it Ubuntu decompresses the kernel and starts to boot. However it doesn't get far, it displays the following message:

4294676.933000 Kernel panic - not syncing: Attempted to kill init!

It then hangs and won't boot any further. I'm fairly sure that the names and path of the kernel files are correct...

Does anyone have any ideas?

---

### Post by steve.horsley on 2006-05-22
Those kernet options look suspicious to me. Here's an extract from my menu.lst...
> title           Ubuntu, kernel 2.6.15-23-k7
root            (hd0,6)
kernel          /boot/vmlinuz-2.6.15-23-k7 root=/dev/sda7 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-k7
savedefault
boot
And on that basis, I suggest yours should look something like this:
> title Ubuntu (2.6.12-10-386)
root (hd0,0)
kernel /boot/vmlinuz-2.6.12-10-386 root=/dev/hda1 ro quiet splash
initrd /boot/initrd.img-2.6.12-10-386
boot
You may need to say sda1 rather than hda1, depending on your hard disk type.

---

