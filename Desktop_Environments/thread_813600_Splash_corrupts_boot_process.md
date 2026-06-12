---
title: "Splash corrupts boot process?"
date: 2008-05-31
forum: Desktop Environments
---

### Post by sderrick on 2008-05-31
I have recently been experiencing problems with Ubuntu.  I was running 7.04 and after booting sometimes the video would be screwed up, my sound didn't work any more.  And instead of the single drum roll heard when with the display of the login window, I would hear 3 rolls followed by a very faint repetition.  I then upgraded to 8.0, scary but it succeeded. 
Still the problem with the video and sound.  

I then tried using the "recover" boot option.  Using that selection and then selecting "resume normal boot" when the recovery menu comes up resulted in a normal boot. Video was fine and sound works!  I have two boot options in the grub menu.

title		Ubuntu 8.04, kernel 2.6.24-16-generic Desktop
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3cbae6da-04f0-4a4d-85ca-7e1a2933bfb8 ro splash pci=noacpi noresume
initrd		/boot/initrd.img-2.6.24-16-generic
quiet

title		Ubuntu 8.04, kernel 2.6.24-16-generic Desktop (recovery mode)
root		(hd0,2)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=3cbae6da-04f0-4a4d-85ca-7e1a2933bfb8 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

Everything is the same but a few things on the kernel line.  I tried a few combinations and figured out if I remove the "splash" option from the normal boot, everything works as it should.

Anybody have an idea why the splash option would do that?  

Any ideas on how to restore the splash process to its original settings?  The first 6 months of using Ubuntu worked great with no problems.  

Scott

---

