---
title: "Extending main partition with extra space from separate hdd?"
date: 2006-04-12
forum: Desktop Environments
---

### Post by green1152 on 2006-04-12
I am using quite an old computer with a very odd setup. The main hard drive (sda) is only about 3 gigs, and I have an extra slave drive (hdd) which is about 120 gigs. I know for a fact that if I want to do some updates on ubuntu that I would need more space, and I've already been down that path more than once by trial and error.

Is there any way I can use a seperate partion from hdd to extend the measly 3 gigs on sda?

I've read around a bit and found a couple things. Gparted and parted in terminal, but the criteria didn't quite fit my needs.

Thanks in advance. This would help a lot.

---

### Post by Ampersand on 2006-04-12
Would it be possible to make a 10Gb partition on the 120Gb drive, and use that for the / directory, with the rest of the drive being /home or something? The 3Gb drive could then be used for the swap partition, or /tmp.

---

### Post by green1152 on 2006-04-12
well, I suppose so, but I have weird issues with grub if I install it on the slave drive.

For some reason the main drive doesn't route through the motherboard, it routes through some card that is on the motherboard, and the IDE ribbons are completely crazy.

I'm not sure if that's an issue or not, but the way I have it set up with / on the SDA drive works best... I just need more space. Is there a tutorial for installing it the way you mentioned?... Or similar?

---

### Post by er-ku on 2006-04-12
[QUOTE=green1152]well, I suppose so, but I have weird issues with grub if I install it on the slave drive.

For some reason the main drive doesn't route through the motherboard, it routes through some card that is on the motherboard, and the IDE ribbons are completely crazy.

I'm not sure if that's an issue or not, but the way I have it set up with / on the SDA drive works best... I just need more space. Is there a tutorial for installing it the way you mentioned?... Or similar?[/QUOTE]

First, can't you tell the BIOS of the mainboard to boot from IDE, and leave out SCSI? (I suppose it's SCSI what you're using, cuz i don't think there are 3GB SATA drives out there..) ;)

Then, I'd still suggest you to fiddle with GRUB/boot settings a little bit more. I have a working server that boots from /dev/sdg and has root partition on it. It didn't work right from the first time, but I managed to make it work somehow.. :) I don't think it's impossible to boot from the big drive in your situation.

---

### Post by mchatel on 2006-04-12
Ubuntu comes with LVM support in it (logical volume mangement), so that may be an option to meet your needs.  There is a bit of a learning curve to it, but it's no more complicated than partitioning.  LVM would easily allow you to allocate empty space off one drive, to extend another volume on the first drive.  Very flexible.

I use it.  I love it.

---

### Post by green1152 on 2006-04-12
Thanks for the replies. I'll check out the LVM idea first. I have already probably reformatted and reinstalled atleast 5 times just from learning how to use ubuntu. Thanks for the replies.

---

