---
title: "Fglrx broken after a hard power off"
date: 2006-03-06
forum: Desktop Environments
---

### Post by cybermatthieu on 2006-03-06
Hi,
Last night I accidently puched the single button on my UPS, so it resulted with a hard power off my computer. After rebooting, XORG seem to be broken (only onw of my monitor was working and it was not on a good resolution). So I changed the driver to Ati, now X was ok but no dual display and/or accelerated graphics. I then tried to change the driver back to fglrx. The problem remained.

After unistalling fglrx (the X package and the kernel one (restrited modules)). I tried to fire up X, the problem was still there.

I then tried to reinstall several package, the X server was reinstalled with no success.

Is there any lib that could cause this problem? I think it could be related to the arpgard module, how could it be reinstalled? Is there anyonw who had this kind of probleme before? I'm seriusly thinking of reinstalling...

Thanks,
Matt

---

### Post by cybermatthieu on 2006-03-07
Hi again,
I reinstalled ubuntu last night. And guess what, IT'S STILL BROKEN!

At first, I thought, O well one of my card is fried... But listen to this. If I boot in windows, the video card works perfecly. I know it's not linux.. so hear this. I loaded Gentoo and every thing is fine!

I fooled around with my box a bit, and I figured out that it had to do with my TVTUNER (Ati Tv Wonder). If I remove it from my system Ubuntu works with fglrx. If I put it back in the same PCI slot, it comes back. But last night I tied to put in an other PCI slot, and it worked! I was able to watch some tv and one DVD. But today when I rebooted my machine, the problem was back.

I really don't get this. It's the weirdess computer problem I ever had! Is there any issue with the ATI TV WONDER in Ubuntu? I hope that I'll be able to fix this...

Thanks,
Matt

---

### Post by cybermatthieu on 2006-03-10
Hi,
Apparently it's a kernel related problem. I built my own custom kernel and the original problem is gone. Now the fglrx driver is not responding to the configuration. It's suppose to be a dual driver configuration but insted it's showing in clone mode. I had this issue before in Gentoo, it's kernel related.

Is there anyone who had this kind problem?

Thanks,
Matt

---

### Post by cybermatthieu on 2006-03-10
Delete

---

