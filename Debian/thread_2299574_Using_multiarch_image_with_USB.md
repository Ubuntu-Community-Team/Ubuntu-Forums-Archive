---
title: "Using multiarch image with USB?"
date: 2015-10-19
forum: Debian
---

### Post by qyot27 on 2015-10-19
I've got one of those wonky Bay Trail-T Mini-PCs* that have a 64-bit processor (Atom Z3735F) but 32-bit UEFI firmware due to shipping with a 32-bit version of Windows to conserve space or be less expensive or whatever the reason is.  And while I can successfully make a LiveUSB of 64-bit Ubuntu 15.10 and boot from that by inserting the bootia32.efi file into the right directory on the flash drive, trying to install from it is not successful, so I went looking for alternatives, and found out that Debian itself apparently added support for this weird combination with the multiarch images for 8.0 and that the setup discrepancy should be automatically detected and the install should work like you would normally expect.

So I grab the multiarch ISO, use Rufus to write it to the flash drive I'm using as the install media, and reboot.  GRUB on the USB fails, though, so I can't even launch the installer.  I have no clue where to go from here.  When I tried the standard amd64 Debian netinst ISO (before realizing it's only the multiarch image that supports this), that actually did let me boot into the installer, but it didn't seem to detect the SD card I'm using as the install target.  And while the multiarch image would probably have the same issue, I'd at least be under the correct version to be able to address the problem prior to install.

Worse comes to worst, I could always just use Debian 32-bit, but I'd rather not since the CPU is 64-bit (and while the CPU may be anemic by current standards, it does have all the way up to SSE4.2, and if I wanted to encode stuff in HEVC using x265, you can only enable the assembly optimizations when building as 64-bit, plus it looks like there's *decoding* benefits in libavcodec for HEVC's SIMD opts when built as 64-bit, so there's that when I actually want to play said files).


My plan is to install to a 64 GiB Class 10 UHS-I U3 SD card, since that could potentially get me better performance than booting from USB 2.0 (due to performance minimums required by the SD specs and whatnot), plus the SD card's storage space is larger than all of my USB flash drives put together.  I don't yet know if this device* can even boot from an SD card, since I've yet to have an install finish correctly.  But if it can, it'd also be less cumbersome since the extra USB port would be available for regular use.

*the [Quantum Byte](http://www.quantumsuppliers.com/shop/products/quantumbyteminipc/), for anyone wondering.

---

### Post by arochester on 2015-10-20
Maybe a clue lies in [http://www.cnx-software.com/2015/02/13/how-to-install-ubuntu-15-04-on-mele-pcg03-intel-mini-pc/](http://www.cnx-software.com/2015/02/13/how-to-install-ubuntu-15-04-on-mele-pcg03-intel-mini-pc/)

Particularly "Make sure Rufus has selected the right Device, and click on &#8220;Start&#8221;.

Once this is done, you&#8217;ll need to download bootia32.efi, and copy it in /EFI/BOOT folder in the USB flash drive.

Now connect the USB flash to your MeLE PCG03 or other Intel Bay Trail-T device, power the device, press F7 to get to the UEFI menu, and select your USB flash drive in order to boot into Ubuntu 15.04."

---

### Post by qyot27 on 2015-10-20
That's exactly what I did to get Ubuntu 15.10 64-bit to boot from USB, but Debian was supposed to support it OOB.  Turns out that the bootia32.efi that the Debian images come with has some issues on this hardware; switching to the other one made it work (although that's still no guarantee I can get it installed and booting from an SD card).

---

