---
title: "dell inspiron duo windows 7 dualboot"
date: 2011-12-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by unfuquitable on 2011-12-11
I have completely reformatted my HDD, and have no windows 7 to dualboot. how do i get that back from within ubuntu. Ubuntu 11.10 is the only system i have installed here?

---

### Post by teh603 on 2011-12-11
If you don't have an optical drive, or even if you do and you don't have a Win7 recovery CD, you're kinda SOL. I don't know if they come with the recovery CD, but I do know they don't come with optical drives.

Edit: Here's how to be able to dual- boot, although Ubuntu will be the default.

1. Start with a fresh install of Windows 7 from your recovery CD. You'll need a USB optical drive. You have to use the recovery CD, because the OEM install of Win7 has all your hard drive's partitions maxed out. By reinstalling from the recovery CD, you force Win7 to exist on only one partition.

2. Start the installer of your Ubuntu flavor of choice. When you get to the partitioner, select the option for "install alongside the existing stuff, picking whichever one you want on startup." This one is probably unavailable with the OEM install, because of reasons listed above.

3. Let the installer do its thing. I've seen it take up to an hour on a slow system. Have some tea, watch some TV, read a book, do something else. If the screen goes black, hit Shift on the keyboard to wake it back up.

4. Reboot into Ubuntu. Run the updater, install any drivers if necessary, and so forth.

5. Reboot into Win7. Wait an hour or two while it checks the drive. Run the updater, install drivers, and all that.

At this point, you're pretty much done.

---

