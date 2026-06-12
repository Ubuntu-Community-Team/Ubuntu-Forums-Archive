---
title: "Grub Trouble, LVM, Fedora Setup..."
date: 2006-07-29
forum: Desktop Environments
---

### Post by peabody on 2006-07-29
Yikes!  You know what, I meant to add this to the Desktop Support forum for the latest Ubuntu, but I ended up posting it here by mistake.  Could A mod move this thread?  I'd greatly appreciate it.

Hi folks.  I'm a long time Linux user who was running Fedora Core 4.  I'd been hearing great things about Ubuntu for a while so I got the crazy notion to just randomly try it out one night.  Trouble was I knew I was running on a slightly non-standard partitioning setup.  Coming from Fedora, I had decided to use LVM.  My partition setup is as follows: One ext3 partition on /dev/hda1 which is where /boot is mounted, which is needed since grub or lilo can't boot from an LVM logical volume.  Both /dev/hda2 and /dev/hdb1 are LVM partitions where I have my Volume Group "SamsDisks" made up of three ext3 partitions, /, /home, and swap.

Like most terribly lazy folk, I didn't really have a good backup of my /home partition, and didn't feel like making one (really bad I know, save me the lecture).  I wasn't sure if Ubuntu would be happy with my setup, so I tried the #ubuntu chat room on freenode to ask a few questions.  I was told that Ubuntu did support LVM, but that I would probably want to try the alternate cd.  So I downloaded and installed from the alternate CD and I'm happy to report that I'm typing this to you now from my brand new Ubuntu install and I haven't lost anything.

However.

I did kinda go through a lot to get here, namely, I couldn't get Grub to work from the MBR on /dev/hda.  When grub tried to boot, it would print:

GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB GRUB...

For all eternity across my screen.  Which was kind of cool, but wasn't going to get me a booted into my system.  After futsing in shell-land via the resue shell for a long time, I managed to get grub installed on a floppy with this incantation:

grub-install --root-directory=/boot /dev/fd0

I was finally able to boot into my system, with following magical incantation from within grub booted from the floppy:

root (hd0,0)

kernel /vmlinuz root=/dev/mapper/SamsDisks-root

initrd /initrd.img-2.6.15-23-386

boot

I made the /boot/vmlinuz link from within the rescue shell.  So I'm up and running now, my original user folder intact and all.  It's like I never changed systems.  Still, I'd really like to figure out what I need to do to get grub working.  It worked under Fedora, so I'm sure there's a way to get it working within Ubuntu.  I suppose I could bury myself within the grub documentation for a day or so, but I have a Chemistry final in less than seven days and a lab notebook that needs finishing, so I am slightly pressed for time.  Has anyone else experience with this sort of thing.  All advice is greatly appreciated.

---

