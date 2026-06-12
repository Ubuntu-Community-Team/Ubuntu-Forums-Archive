---
title: "64bit Lubuntu won't boot after install. PC has no UEFI or Secure Boot options in bios"
date: 2020-07-17
forum: Desktop Environments
---

### Post by theconceptboy on 2020-07-17
Hello everyone.
I'm trying to install lubuntu to take advantage of the lightweight OS. The 32 bit OS version installs just fine from a flash drive and operated flawlessly. However I need a 64 bit one and that one does not install so well. Where the 32 bit one can be installed directly from the USB drive boot menu, the 64 bit has to be installed via the installation tool from within the flash drive bootable OS . This computer is a dated Intel Q8300 with a DQ3510J_ motherboard. It has no UEFI or secure boot options in the bios which so many answers on the internet seem to refer to when it comes to fixing the boot failures.

I used the following settings when burning the bootable drive:
[IMG]https://i.snipboard.io/d8uTBX.jpg[/IMG]

How do I install the 64 bit lubuntu OS to get it up and running on this machine? I use the 3rd partitioning option during the installation which erases everything from the drive. What am I missing?

Thanks fellas.

---

### Post by guiverc on 2020-07-17
You haven't said what Lubuntu release you have attempted to install.

I also don't know what the "*life OS installation tool*" is.

 The intel c2q q8300 shouldn't be a problem, as I'm using a c2q q9400 and running Lubuntu *groovy* (and this box has run all since *artful*/17.10)

The *third partitioning option* isn't very helpful, as we don't know your Lubuntu release (or your ISO if using 18.04). Lubuntu currently has 3 different supported installers, chosen when you grab the ISO, but you didn't tell us your release so we can't narrow it down to which installer you used, or if you had choices. We need some more details  (*or at least I do*)

---

### Post by guiverc on 2020-07-17
Okay, I now see a picture.

I'd forget about Lubuntu 19.10.  It reaches EOL (*end-of-life*) at the end of today, so for starters, download and try installing Lubuntu 20.04 LTS.


FYI:  Lubuntu 19.10 was the 2019-October (Ubuntu uses a *year.month*) format for all server & desktop releases, and standard releases have 9 months of supported life, that 9 months is up today for 19.10.  Lubuntu 20.04 LTS however is a *long-term-support* release, and thus has 3 years of full support, so makes much more sense for most users. (5 years applies to main Ubuntu, parts of Lubuntu 20.04 LTS have 5 years of support, but other parts only 3 years).

---

### Post by theconceptboy on 2020-07-17
Thank you for a quick response. I've gone ahead and downloaded the 20.04 release. Falshed it onto an flash drive and installed the OS. The boot issue still persists:

This is the source where I downloaded the OS:
[https://lubuntu.me/downloads/](https://lubuntu.me/downloads/)

Flashed onto a USB stick using these settings:
[IMG]https://i.snipboard.io/TSpkZV.jpg[/IMG]

When installing, this these are the options I chose: When I mentioned I used the 3rd option, this is what I was talking about. 
[https://imgur.com/a/8KSgyvL](https://imgur.com/a/8KSgyvL)

[IMG]https://i.imgur.com/QAgLPk2.jpg[/IMG]

Is there any other info I can fetch to help diagnose this problem?

I also get this option, as recomended by the dialogue box that seems to be meant to address this issue:

[IMG]https://i.snipboard.io/G7miPC.jpg[/IMG]
But I'm pretty sure that's just for issues with the booting from the flash drive.

---

### Post by theconceptboy on 2020-07-17
Perhaps I need to manually set up the partitions myself instead of letting linux do it? I think I saw something about that auto-partitioning tool not doing it for some people..

---

### Post by guiverc on 2020-07-17
I've had the most success with the "*erase disk*" option you used. The only times it didn't work for me, were issues with BIOS/UEFI settings being incorrect and that was UEFI netbooks.

Known issues with the installer are documented in our release notes ([https://lubuntu.me/focal-released/](https://lubuntu.me/focal-released/)) and I don't think any apply.

I can't offer any advice with Rufus though, as I've never used it. I believe the write to media is not your issue though (as you indicated too!), as media-write issues usually mean the live-system/installer won't boot, your issue is you cannot boot into the installation post-install which is a different issue.

The only issue I can think of currently is a BIOS setting that prevents the MBR from being written (*ie. a security option that causes any program to think a write succeeded thus no errors are shown, but prevents the write from occurring, thus OS won't boot*). How this option appears however varies on the BIOS on your motherboard and that I don't know sorry. It's my only thought.

---

