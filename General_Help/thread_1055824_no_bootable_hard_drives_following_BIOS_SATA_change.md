---
title: "no bootable hard drives following BIOS SATA change"
date: 2009-01-31
forum: General Help
---

### Post by daking874 on 2009-01-31
Hi,

I have been trying to get my ubuntu intrepid to play commercial DVDs (another story) and the final piece of advice I found was to change the BIOS settings to use SATA compatibility mode (from enhanced mode).

This I did and ubuntu failed to boot computer. My computer has 2 HDs- 1 small for the OS and a larger one for data. In compatibility mode, only the large HD and cdrom was recognised.

So I changed it back to SATA enhanced and now the bootup screen somes up with "please select a proper boot device..."

I've checked the BIOS screen. Primary IDE Master: large (data) drive; Primary IDE Slace: cdrom; Third IDE master: small (OS) drive.

I have hit F8 and manually selected the small drive for boot and then it just blank screens with the HD doing something.

My PC is an ASUS P3-PH4C which asus has put together with old components but was working fine before this (save the DVD thing).

I now have to boot from cd.

Any advice gratefully received.

---

### Post by daking874 on 2009-01-31
I've just used fdisk and it tell me the small drive is now recognised as device sdb1... I'm pretty sure it was sda1 previously so seems like a hardware issue still so perhaps a BIOS problem.

I could just switch the cables on the HDs around.

---

### Post by daking874 on 2009-01-31
I solved this by booting from Live CD and using the sudo grub command to reestablish the boot record.

It has some extra messages but boots up fine. AND will now play DVDs (go figure as far as I can tell I restored it to it previous state BIOS-wise).

---

