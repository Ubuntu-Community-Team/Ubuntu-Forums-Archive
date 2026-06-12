---
title: "USB Thumb Drive Won't Boot No More  :("
date: 2009-06-12
forum: General Help
---

### Post by t0p on 2009-06-12
A while ago I used UNetbootin to make a bootable live usb stick with BackTrack 3 on it.  I used it for ages, it was fine.  But recently I decided to put Jaunty on it, so I could install the jackalope to my Eee.  I did that, and it booted fine, and now I have Jaunty on my Eee and Hardy on my desktop machine.

But I missed BackTrack.  So I decided to make the thumb drive back into a botable live usb of the wicked hacker's OS.  I used UNetbootin to install an .iso that I had on my hard drive.  But it wouldn't boot.  Whether I put up the "boot" flag or not.  So I downloaded an .iso of BackTrack afresh, and used UNetbootin to put that one on the usb drive.  Yet still it won't boot!  It's definitely something to do with that drive, or with UNetbootin, or something, cos the so-called bootable live usb will not boot on my desktop machine or my Eee.  I don't get it.  Why's this happening??  The .iso gets written to the stick seemingly okay.  But it just won't boot>!!  :(

Is it possible for a once-perfectly-fine usb stick to suddenly become non-bootable?  I can write files to it okay.  But it won't boot!!  And I don't have another to try at the moment....

Why oh why is this happening?

---

### Post by nothingspecial on 2009-06-12
Which version of unetbootin are you using. I had this problem earlier this year. Try the version from the Jaunty repos if you`re not already using it.

If you are then I don`t know.

---

### Post by t0p on 2009-06-12
> **nothingspecial said:**
> Which version of unetbootin are you using. I had this problem earlier this year. Try the version from the Jaunty repos if you`re not already using it.

If you are then I don`t know.

Well, I've been doing all this on my hardy machine, so its the hardy version of UNetbootin.  I shall try it on my jaunty machine.  Cheers for the tip!

---

### Post by rCXer on 2009-06-12
How long have you been using the drive? Have you tried another one?

Unlike hard drives, USB Thumb Drives use flash memory that can wear out.  Usually this takes 10,000-100,000 read/writes per memory cell.  This is nearly impossible to reach if the drive is simply used to backup files but by running an operating system (or 2) this limit can be attained.  An article on this can be found [here](http://ablog.apress.com/?p=344).

This has happened to me before. You may need to replace the drive.

---

