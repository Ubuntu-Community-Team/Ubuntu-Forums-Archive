---
title: "Unable to boot to Windows 7 partition."
date: 2012-02-09
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Grafeit on 2012-02-09
Dell OptiPlex - 380 - 3 GB RAM - 2.93 GHz

I installed Ubuntu 11.10 on my Dell with Windows 7 and now I can't boot to the windows partition. I can't seem to figure how to specify what partition the computer boots to. I know how to get to the bios and tell the computer what order to boot in, and how to get to the boot manager to select a device, but it only shows the HDD, it doesn't show the various partitions.

---

### Post by mikewhatever on 2012-02-10
Can you boot Ubuntu? If so, open a terminal window (ctrl+alt+t),
 type **sudo fdisk -l** and post the output.

---

### Post by Grafeit on 2012-02-11
> **mikewhatever said:**
> Can you boot Ubuntu? If so, open a terminal window (ctrl+alt+t),
 type **sudo fdisk -l** and post the output.

Will do. I will try that as soon as I can!

*Edit*
Actually, that is just a command to list partitions right? I can see the windows partition in the home folder, I can access all of the files, I can unmount it, I can save to it or copy from it...I know the partition is there.

Also, holding shift doesn't work for some reason...When I turn the computer on it boots to a blue Dell screen, then it changes to a black screen, after a moment a dialog window appears that reads something in regards to invalid signal, correct resolution should be 1980x800 (its something with the display), then it boots to my desktop in Ubuntu. I have Ubuntu on a Toshiba and when I boot up holding shift it takes me to a boot manager and lets me select the device AND partition I want to boot to. (even shows Ubuntu recovery mode).

The Dell had some trouble getting software updates, there were about 395 and it kept timing out before all updates could be downloaded. Is there a place to manually download updates?

---

### Post by mikewhatever on 2012-02-11
[bootinfo script]("http://bootinfoscript.sourceforge.net/"), run it and post the output.

As for updates, do you have internet connection on that machine?

---

### Post by Grafeit on 2012-02-11
> **mikewhatever said:**
> [bootinfo script]("http://bootinfoscript.sourceforge.net/"), run it and post the output.

As for updates, do you have internet connection on that machine?

I do not unfortunately.  My modem is fried or Comcast has bad service. (It's been down for 2 days)

---

