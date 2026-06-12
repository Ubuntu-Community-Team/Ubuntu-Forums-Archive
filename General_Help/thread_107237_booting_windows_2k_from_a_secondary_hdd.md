---
title: "booting windows 2k from a secondary hdd"
date: 2005-12-22
forum: General Help
---

### Post by gnu2tux on 2005-12-22
Hi,

 I've dual-booted windows from the same hard drive as Linux was on before without a problem, but I have a need to boot the dreaded 'doze from a separate hard drive for some software testing this week.

I have inserted this in my /boot/grub/menu.lst:

```

title           Windoze 2000
root           (hd1,0)
chainloader     +1

```

It complains of unknown partition type 0x07 and dies. It's an NTFS partition.

The setup is a bit strange, which is probably the cause of the problem:

I have a SATA hard drive (primary drive) which grub/linux is on (/dev/sda) and the drive that windows is on is the primary IDE channel, I can read in Ubuntu as /dev/hda1 (i mounted it in /etc/fstab as /d_drive without issue).

Can you tell me where I'm going wrong - I'm not a grub expert but I'm sure I've had this sorta thing working before without too many problems.

I can boot the ide hard drive normally if I just remove the SATA control information from the BIOS, but i'd rather not feck around with the bios every time i want to boot from the drive!

Cheers!

---

### Post by garba on 2005-12-22
I had a setup which is the same as yours, you need to add the following to the windoz grub entry:

map (hd0) (hd1)
map (hd1) (hd0)

I hope I am not mistaken, it's been a long time since I last felt the need to add a windows xp entry to my grub menu :D :D

---

### Post by gnu2tux on 2005-12-24
Thanks very much - that works great :)

Ali

---

### Post by mztriz on 2005-12-24
[QUOTE=gnu2tux]Hi,

 I've dual-booted windows from the same hard drive as Linux was on before without a problem, but I have a need to boot the dreaded 'doze from a separate hard drive for some software testing this week.

I have inserted this in my /boot/grub/menu.lst:

```

title           Windoze 2000
root           (hd1,0)
chainloader     +1

```

It complains of unknown partition type 0x07 and dies. It's an NTFS partition.

The setup is a bit strange, which is probably the cause of the problem:

I have a SATA hard drive (primary drive) which grub/linux is on (/dev/sda) and the drive that windows is on is the primary IDE channel, I can read in Ubuntu as /dev/hda1 (i mounted it in /etc/fstab as /d_drive without issue).

Can you tell me where I'm going wrong - I'm not a grub expert but I'm sure I've had this sorta thing working before without too many problems.

I can boot the ide hard drive normally if I just remove the SATA control information from the BIOS, but i'd rather not feck around with the bios every time i want to boot from the drive!

Cheers![/QUOTE]

Wait!? This is possible, I don't quite understand. How did you do it!? I have another harddrvie and I was wondering if I could put a differnt os on it say windows or intel mac and add that to my computer with ubuntu. Where do I start? 

Right now I have a 60 gb hardrive with ubuntu if I wanted to put windows on a different harddrive and add it to ubuntu what would I have to do?

---

### Post by gnu2tux on 2005-12-25
This is the way I did it:

disconnected my Linux drive, so that Windows knows absolutely nothing about any other drive, let alone Linux.

Installed Windows in a perfectly normal fashion, booting it from IDE 1, primary channel.

Installed my other drive (SATA -- runs on a different interface than IDE) with Linux on it.

Made the above amendments to /boot/grub/menu.lst and that's all there is to it. If i'd have known the mapping information to begin with, this would be the easiest way to dual boot!

I would imagine the same would apply for an IDE-only PC:

Install new windows drive in IDE2 Master position (whilst having IDE1 Linux drive removed).
Install Windows on that, make sure it boots from IDE2
then insert your linux drive, ensuring that boots, and then make your alterations to grub like before.

Merry Christmas!

---

### Post by mztriz on 2005-12-27
[QUOTE=gnu2tux]

Installed Windows in a perfectly normal fashion, booting it from IDE 1, primary channel.



Install new windows drive in IDE2 Master position (whilst having IDE1 Linux drive removed).
Install Windows on that, make sure it boots from IDE2
then insert your linux drive, ensuring that boots, and then make your alterations to grub like before.

Merry Christmas![/QUOTE] 
Thank you so much but I have no idea what the things I quoted above mean. I know how to get my harrdrive in master but I still don't knwo what you mean by having it IDE2? And does that I mean i make the IDE1 slave?

---

