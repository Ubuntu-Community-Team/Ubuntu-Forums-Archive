---
title: "Intel ips i915 boot error"
date: 2010-10-15
forum: Desktop Environments
---

### Post by Chrison999 on 2010-10-15
Hi, all!

I just recently switched from Fedora 12 to Ubuntu 10.10 because I was  having problems with the ATI Catalyst video drivers in Fedora.  The  Catalyst drivers work just fine with Ubuntu, but I'm getting this  strange error message when the system boots:

```
[   12.983251] intel ips 0000:00:1f.6: failed to get i915 symbols,  graphics turbo disabled
```My graphics performance is "acceptable"  but does seem to be a bit slower than when I was running Fedora (that  is, before Catalyst killed Fedora).  I have read through the Forums and  it appears this is probably a kernel bug, but has anyone come up with a  fix/workaround yet?

Btw, I'm now suddenly also getting this strange boot error:

```

[   13.934309] /build/buildd/linux-2.6.35/drivers/hid/usbhid/hid-core.c: usb_submit_urb(ctrl) failed

```This one just mysteriously started appearing mysteriously this  morning.  Does anyone have any suggestions on how to fix this one?

Thanks, in advance, for any assistance provided!

Regards,

Chris

---

### Post by fdmille on 2010-10-15
This seems to be a kernel issue.  I've tried the 2.6.35-22-generic and the latest RC7 for kernel version 2.6.38, neither work.  I get the grub menu and the flashing curser, and then a black screen after the Intel ips message flashes on the screen for about one second.  I do not get anything if I try to Alt F1 or Alt F6.

However, my system works fine if I use kernel version 2.6.34.  This was the last kernel I used with Ubuntu 10.4.

:(

---

### Post by Chrison999 on 2010-10-16
> **fdmille said:**
> This seems to be a kernel issue.  I've tried the 2.6.35-22-generic and the latest RC7 for kernel version 2.6.38, neither work.  I get the grub menu and the flashing curser, and then a black screen after the Intel ips message flashes on the screen for about one second.  I do not get anything if I try to Alt F1 or Alt F6.

However, my system works fine if I use kernel version 2.6.34.  This was the last kernel I used with Ubuntu 10.4.

:(

Hmmm...  my system continues to boot after both error messages, and *seems* to run fine (although I do have a few "glitches" because it's a new install).  But that's what happened to me with Fedora...  worked just fine until a kernel update and then KABOOM!  So, to try and "fix" that, I stoooopidly decided to try to upgrade from Fedora 12 to Fedora 13 and KABOOM I totally killed it.  :(

Anyway, Thanks for your reply, fdmille.  I guess I won't worry to much about the error messages because at least I don't get a black screen.  Hopefully someone else will read this and provide a solution for you as, obviously, I can't help.

Regards,

Chris

P.S.  What do Alt-F1 and Alt-F6 do and when do you press them?  Just curious!  :)

---

### Post by Mihai Chezan on 2010-10-16
There is a new release (RC8 ) for latest kernel 2.6.36 that seems to do some changes to IPS and i915:

Andy Whitcroft (1):
      intel_ips -- ensure we do not enable gpu turbo mode without driver linkage
Chris Wilson (1):
      drm/i915: Prevent module unload to avoid random memory corruption
Jesse Barnes (4):
      IPS driver: don't toggle CPU turbo on unsupported CPUs
      IPS driver: verify BIOS provided limits
      IPS driver: apply BIOS provided CPU limit if different from default
      IPS driver: disable CPU turbo
Matthew Garrett (1):
      IPS driver: Fix limit clamping when reducing CPU power

---

