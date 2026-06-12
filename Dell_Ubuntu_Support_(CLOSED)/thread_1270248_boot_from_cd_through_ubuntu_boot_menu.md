---
title: "boot from cd through ubuntu boot menu"
date: 2009-09-19
forum: Dell Ubuntu Support (CLOSED)
---

### Post by lzboy4jake on 2009-09-19
Hi.  I installed ubuntu about a month ago on my dell inspiron 15 with dual boot vista.  Love it.  Now I am having problems with vista and I need to boot from the vista reinstall dvd but can't figure out how to boot from a cd with the ubuntu boot menu.  Any advice is GREATLY appreciated.

---

### Post by urugTON on 2009-09-19
I'm a little confused about a few terms you used, so let me take a moment to go through the PC boot process.  I hope I don't insult you by starting at too basic a level.

The BIOS starts up first.  A Boot Loader takes over from there. The Boot Loader eventually passes control to an OS - be it Vista or Ubuntu.  Most likely the Boot Loader you are using is GRUB.  That's what Ubuntu installs from the LiveCD.  You may need to run GRUB after you use the Windows Restore CD, so you'll need to know its correct name.  

The BIOS has a list of boot devices and an order in which to try them.  As soon as it finds a device that has a proper MBR (Master Boot Record), it transfers control to the code in the MBR of that device.  In your case, that code is first part of GRUB.  There are several stages of GRUB, but it is the final stage that gives you the menu allowing you to select Vista or Ubuntu.

If you followed the path I did to dual boot Vista, then you put the Ubuntu LiveCD in the drive, powered on and hit F12 (could be F2, F10) to select the Ubuntu DVD.  The F12 overrode the usual BIOS processing and booted to the MBR on the DVD and brought up Ubuntu.

You need to get the BIOS to boot to the Windows Restore DVD with the F12 while the BIOS is running.  No different than what I did to install Ubuntu. 

My experience says that you need to be very, very careful at this point.  Ubuntu is gracious about sharing the hard drive.  Windows is considerably less so.

You will have the opportunity restore the Vista system to factory defaults.  There's a good chance that will wipe Ubuntu off the hard drive all together, along with your data in Windows.  I have no experience with Vista's Restore DVD nor do I know what problem you are facing.  None the less, I'm pretty certain there are devils lurking there.  Be careful.

Depending on what you do, the Windows Restore DVD may rewrite the MBR. If it does, you'll boot to Vista without the choice of booting to Ubuntu.  At that point you'll need to restore GRUB to the MBR.  Restoring GRUB with the Ubuntu LiveCD is not difficult. The instructions at

[http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11](http://maketecheasier.com/how-to-restore-grub-in-ubuntu/2008/04/11)

look good.  

I strongly encourage you to backup up your critical data before you start this process.  I've trashed hard drives in the process of "fixing" them.  It will be far, far simpler to back your important data before running the restore.  In fact, it may not be possible to get the data after the "restore" process has run.  You can, BTW, get to your data under Vista from Ubuntu.  Post if you need help on that.

Good luck.  Be careful!

Let us know how things came out for you.

---

### Post by lzboy4jake on 2009-09-19
I figured it out.  I just wasn't hitting the F- button quick enough to get to the BIOS menu.

---

