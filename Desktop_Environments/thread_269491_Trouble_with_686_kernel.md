---
title: "Trouble with 686 kernel"
date: 2006-10-01
forum: Desktop Environments
---

### Post by SirShaggy on 2006-10-01
I am installing Dapper for my ex-wife. She bought a new HP m7463 with a Pentium D 3.0 and like 320Gig HD. Anyway, the live CD worked really well, picked up all of the hardware. I installed all updates, the nVidia driver and rebooted. I logged in perfectly. Used it for a week, installed a few other things, java, codecs, swiftfox, frostwire, etc....
All along, everything is fine. Then, I installed the 686 kernel and restricted drivers. I can still boot into the 386 kernel just fine. If I try to select the 686 kernel in grub, it loads quickly to the login screen, my mouse won't move around and I can't type at all. The cursor just sits there flashing. Any ideas? I'd like to get this fixed, she is my ex-wife.....what could come next?!?!?:confused: 
SirShaggy

---

### Post by Mr Frosti on 2006-10-01
Just to clarify, you installed the "kernel-image-x.x.x-686" and the "linux-restricted-modules-x.x.x-686" packages? Also, the version numbers in the "kernel-image" and the "linux-restricted-modules" package are the same?

---

### Post by SirShaggy on 2006-10-01
Yes, I just went in to look, you are correct. I wasn't sure about the kernel versions, but yes, they are the same. Both are 2.6.15-27-686.

---

### Post by SirShaggy on 2006-10-01
Well, I tried to unplug the keyboard and mouse, wait a few sec. and plug them back in. Nothing helped there. I also just tried a different keyboard. That too didn't work. I shut it off, went into the BIOS and enabled legacy support, just for kicks, booted into 386 again just fine, restarted, selected the 686 kernel, still can't login. Maybe something with xorg.conf???
Maybe I need another package or to configure something???

---

### Post by SirShaggy on 2006-10-01
While I was typing the last post, she installed the 64bit Ubuntu CD and booted it just for kicks. It loaded to the login screen and the same issue, no mouse or keyboard. Makes me think it's hardware related, but it works in regular 32bit 386 kernel. I'll keep playing around. Post any ideas you might have. We can still boot into 386 kernel to make repairs or adjustments and she can play a bit. It has to be a quirk.
SirShaggy

---

