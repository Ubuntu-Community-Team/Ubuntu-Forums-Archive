---
title: "Grub error 17 on drive addition"
date: 2009-04-01
forum: General Help
---

### Post by fyo on 2009-04-01
I have a system with 2 SATA drives, running Ubuntu 8.10 with no problems. However, when I add an old ATA drive, grub spits out an error 17 (i.e. doesn't boot).

Reading up on the subject, it appears that grub and my BIOS don't agree on the order of the drives, so when grub tries to boot Ubuntu, it thinks it's on a different drive than it really is.

The only suggested fix I've been able to find (other than setting "Mode: User" in BIOS which doesn't work for me) involves manually editing /boot/grub/menu.lst and/or /boot/grub/device.map.

I'd REALLY rather not do that - and even if that were the only solution, I'm still not clear as to what I should modify (or, rather, what I should modify "it" to).

If anyone knows of a way to solve my problem... I'd much appreciate it.

I can boot from a rescue CD (well, Jaunty Beta on a usb flash card), so I have access to the usual tools. Removing the old ATA drive solves the grub problem (but still leaves me without access to the ATA drive, of course, which is what I wanted to accomplish in the first place).

```
device.map:
(hd0)   /dev/sda
(hd1)   /dev/sdb
```

```
menu.lst (snippet):
title       Ubuntu 8.10, kernel 2.6.27-11-generic
uuid        a4f46dd7-123a-4a3f-b123-c3b44cbabefb
kernel      /boot/vmlinuz-2.6.27-11-generic root=UUID=a4f46dd7-123a-4a3f-b123-c3b44cbabefb ro xforcevesa quiet splash
initrd      /boot/initrd.img-2.6.27-11-generic
quiet
```

(since menu.lst uses uuid's in 8.10, unlike 8.04 which used designations like "root (hd0,1)", I don't see how it could be a problem in menu.lst)

---

### Post by ryanhaigh on 2009-04-02
Rather than changing device.map directly you can boot your broken system, press esc to get into the grub menu if necessary and press E to edit the first entry. You will likely notice that the root line still references (hd0,0). I would guess that the ide device is being identified as hd0 now so if you press E again to edit the root line so that it reads (hd1,0) then press B to boot with the selected options you should be good to go (for that boot at least).

Once booted you should be able to edit menu.lst permanently. Note that whilst the root partition for your kernel entries uses the UUID the groot option still uses (hd0,0). I am not an expert when it comes to these things and don't have the time to try it myself right now but I think if you change that and then perform a grub install you should be able to boot next time.

---

### Post by fyo on 2009-04-02
Okay, so I couldn't do anything with grub since it doesn't get to the menu or anything. It just fails with the aforementioned error, no activity possible. However, I could boot from my "live USB" thumb drive and mess around.

The following worked from the Jaunty live CD (on USB):

$ sudo grub
grub> find /boot/grub/stage1
-> (hd0,1)
-> (hd1,0)
(okay, I apparently have grub on both my SATA drives)
grub> root(hd1,0)
(this is the SATA drive I want to boot from. The other one is an old one left over from a previous Ubuntu install).
grub> setup (hd1)

And then just a reboot.

So far so good. The really odd thing now is that if I do the same thing from Ubuntu (regular boot instead of the Live CD), I get:
grub> find /boot/grub/stage1
-> (hd1,1)
-> (hd2,0)

i.e. incremented by 1. The PATA drive was NEVER removed, so I have no idea why it suddenly renumbered them.

Somewhat annoyingly, my drives in Ubuntu have also been renamed, so that sda is the PATA drive, sdb the previous sda and sdc the previous sdb (the latter two being the SATA drives).

I can't help wonder what will happen if I pull the PATA drive... which I *will* do pretty soon. I just wanted to get everything off it before using it for something else.

I can't help but think this is a really, really lame way of handling drives. The UUID usage in menu.lst has helped and probably saved my bacon (or, rather, prevented me from having to manually changing the drive names from hdb to hdc). I hope something similar is possible in grub at some point, because the situation now is just not tenable.

---

