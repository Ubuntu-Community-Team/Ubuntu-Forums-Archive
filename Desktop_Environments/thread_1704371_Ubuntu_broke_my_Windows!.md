---
title: "Ubuntu broke my Windows!"
date: 2011-03-10
forum: Desktop Environments
---

### Post by dangloverenator on 2011-03-10
Hey people.

So, I'm having a rather major issue with my HP Pavilion laptop, it would be awesome if someone could help me out.

Basically, after a failed attempt at using Kubuntu, I did a completely clean install of Ubuntu alongside my Windows 7 system. Ubuntu works, GRUB works, everything on the Linux side is running perfectly.

The problems start when I try to load my Windows 7 partition: I get a CHKDSK screen that counts down from 10 to 1... and then stops, leaving a hard shutdown as the only option.

Now, I also have a Windows Vista bootloader, which should boot to the Windows Recovery Environment, but when I try and run it it prompts me for a Windows disc (which I don't have), and more interestingly, tells me that it can't gain access to the disk drive.

So what seems to have happened is that my Win7 partition isn't mounting/turning on/being available (or something) at startup. Is that possible/fixable?

Sorry for the bad description of the problem, but I hope someone can help me. Also, if this belongs in a Windows forum rather than an Ubuntu one, please let me know where I should post.

Thanks,

Dan

---

### Post by runeh76 on 2011-03-10
Hi

If u are sure that u didnt harm ur Win partition, then follow next link part *16 Restoring GRUB2 / XP / Vista / Win 7 Bootloaders* 

[http://ubuntuforums.org/showthread.php?t=1195275]("http://ubuntuforums.org/showthread.php?t=1195275")

---

### Post by dangloverenator on 2011-03-10
Hey, thanks for the quick reply. I've (sorta) fixed it now, though.

Incredibly, the problem was actually related to my USB pen, of all things!

I used a USB stick to install Ubuntu, and then removed it once I had installed it successfully. But for some completely unknown reason, CHKDSK wouldn't finish until I put it back in again!

What makes it more annoying/bizarre is that GRUB doesn't load at all (I get stuck on an HP splash screen) until I take the USB stick out.

So to boot into Windows, I had to turn on the computer (without the USB stick), select the Win7 option from GRUB, quickly jam the USB stick back in and let CHKDSK do a completely pointless countdown before loading Windows.

I'm glad that nothing is "broken" as such (my Windows files are all here and everything), but can anyone explain what on earth is causing these bizarre issues?

Dan

---

### Post by dangloverenator on 2011-03-10
Wow, well for some reason, I restarted yet again, kept the USB stick plugged in for the whole time, CHKDSK actually ran, booted into Windows and everything was fine. I can now boot into any OS without the USB stick being plugged in. For absolutely, literally NO reason.

WEIRDEST. THING. EVER.

Anyone want to tell me why this happened? Just out of curiosity?

---

