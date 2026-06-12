---
title: "Moving current Ubuntu installation onto SD card or flash drive and making it bootable"
date: 2009-04-17
forum: General Help
---

### Post by BadGuitarPlayer on 2009-04-17
So I recently got an Asus EEE PC, and I wiped the default linux OS that came with it and installed Ubuntu immediately... But now after playing around with it for a while, I've decided that it would be better for this particular machine to have Windows XP installed as the main OS... but I don't want to lose my already-configured Ubuntu installation, and I sure don't want to be stuck using Windows for good.
So what I want to do is take my current installation of Ubuntu, with all of the apps I've installed and settings I've set, and move it onto my 8 gig SD card (or a flash drive would work just as well I guess) and be able to boot from that. Windows will be on the main hard drive.
I've read about backing up and restoring Ubuntu, and I've read about ways to make a clean Ubuntu install bootable from a separate drive... but never the two combined.
Any help would be greatly appreciated! Thanks!

---

### Post by riza hylviu on 2009-04-17
with remastersys you can backup your system in a  bootable live cd/dvd, then you have only to copy it to your sd card. Are you sure that you can boot from a sd card? A usb drive maybe is a better choice.

---

### Post by trlkly on 2009-04-17
If you can't boot a SD card, you may want to play around with boot loaders that would be able to. You'd load them on the hard drive, but it would then switch to the SD card when you chose to boot Ubuntu.

---

