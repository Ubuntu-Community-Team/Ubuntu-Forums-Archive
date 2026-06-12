---
title: "Better than VGA graphics with VirtualBox W2K guest on Ubuntu?"
date: 2007-11-06
forum: Desktop Environments
---

### Post by wkulecz on 2007-11-06
Got Virtualbox installed on 6.06 without issues, created a virtual machine and installed Windows2000sp4.  Smooth as silk.  However it will have been a total waste of time if I can't figure out how to get better than 800x600 16-color VGA display on the guest OS.

What am I missing?  Surely Virtualbox wouldn't get such rave reviews with this showstopper of a  limitation.

--wally.

---

### Post by wkulecz on 2007-11-06
I did Devices->InstallGuestAdditions from the Virtualbox window and expected something to happen.

Turns out I'm not sure what this does if anything.  But I can now get a nice virtual Windows display (1280x1024, 16-bit color) after installing the Guest Additions.  Seems you have to mount the CDROM ISO image installed as part of the package and then run the setup program from windows.

Hope this is of use to someone else.

--wally.

---

