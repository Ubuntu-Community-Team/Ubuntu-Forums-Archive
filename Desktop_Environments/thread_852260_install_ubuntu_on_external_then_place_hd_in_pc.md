---
title: "install ubuntu on external then place hd in pc?"
date: 2008-07-07
forum: Desktop Environments
---

### Post by finest on 2008-07-07
is it possible to install ubuntu on an external then place the hard-disk from the external inside a desktop pc?

---

### Post by timcredible on 2008-07-07
should be able to without issues, but probably need to change /boot/grub/menu.lst line that you boot with from (hd1,x) to (hd0,x).

---

### Post by Herman on 2008-07-07
We *should* be able to. 

I tried that a long time ago and I do remember having some weird problems with my partitions being recognized. It was quite interesting, I would need to experiment with that all over again to be sure about what I'm talking about. 

If I remember correctly, I removed the hard disk from my laptop because it had Windows XP in it as well as Ubuntu, and I wanted a new hard disk just for Ubuntu. 
I placed the old hard disk inside my external USB hard disk caddy as a FAT32/Ext3 external drive. There was some problem with it about the last track being (or appearing), to finish after the end of the hard disk. Then I think I pressed a button on the front of the USB caddy and that re-aligned my partitions and fixed it, or did something to the BIOS inside the hard disk firmware possibly. I'm not sure, it was a long time ago now.

On placing it back inside my laptop some time later, (like a couple of years or so), it wouldn't boot and the hard disk came up as blank and unpartitioned in GParted. I had a devil of a time getting it to be recognized. I forget now what I did, but I do recall that I had some data backed up in there in a partition that had long since been deleted which turned out to be very valuable to someone else and which needed to be recovered urgently and I think I fixed it with TestDisk. Anyway, I fixed it somehow, because Windows is bootable again in it, (although I rarely if ever boot into it). 

I would be interested to hear back from anyone else who has tried swapping their hard disks between their computer and an external USB drive. 
I'm not sure, but maybe only be my particular brand of external drive has this problem, it has some firmware of it's own of course, and that strange 'reset' button on the front. I haven't seen that on other brands of USB enclosure. Probably most other people can move their hard disk from PC to USB enclosure without a hitch. My new external USB enclosure doesn't have any buttons on the front of it. I'm not sure what that button really does, it seems to shift the hard disk geometry by one track or something. I should investigate that when I have time.

---

