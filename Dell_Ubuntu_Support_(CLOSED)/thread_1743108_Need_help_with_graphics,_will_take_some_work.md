---
title: "Need help with graphics, will take some work"
date: 2011-04-29
forum: Dell Ubuntu Support (CLOSED)
---

### Post by aeronutt on 2011-04-29
I'm having problems with Natty, my Dell Vostro 3550, and graphics. Lot's of trial and error to get to where I'm at, but I'm crawling towards a solution. Here's my current state:

Hardware:
Dell Vostro 3550, Intel i3 with integrated graphics, and AMD Radeon discrete graphics (HD 6630M).

Software:
Ubuntu 11.04 64bit, up to date, no significant s/w or settings changes other than described below. (So far, I've experienced the same problems on both 32 or 64 bit.)

I've been playing around with grub boot options, with the following odd results:

BOOT OPTION.................GRAPHICS BENCHMARK...........MONITOR
<as installed from CD>......------system won't reliably boot----
radeon.modeset=0............12-14 seconds....................recognized
i915.modeset=1................12-14 seconds...................not-recognized
radeon.modeset=1............5-6 seconds......................not-recognized

In short, from the benchmark results, I'm not sure the Intel integrated graphics is working at all, and I can get the radeon graphics working, but the monitor isn't recognized and has wrong resolution.

Ideas?

Would love to figure all this out as a learning experience, and to help others with similar problems.

---

### Post by aeronutt on 2011-04-29
Specific question, I ran:

```
glxinfo|grep render
```

which returned:

```
direct rendering: Yes
OpenGL renderer string: Mesa DRI Intel(R) Sandybridge Mobile GEM 20100330 DEVELOPMENT 
```

Does this change what I might need to add to the boot options to insure Intel sandy bridge integrated graphics is working? For example, should
i915.modeset=1
be something else?

---

### Post by aeronutt on 2011-04-30
I continue to give Unity a try, and I'm finding a few things I really like about it. BUT, a killer for me, is when I type in the search box, it's VERY slow. 2-3 seconds delayed response between every few keys typed. Even just hitting backspace usually delays a few seconds. 

Any ideas?

---

### Post by aeronutt on 2011-05-02
Are others not having this problem, or are you simply accepting it as not a problem, or is it a known bug? Any opinions?

---

### Post by vanadium on 2011-05-02
For me it works acceptably fast: there is some delay in response of the searched items, but human typing is also not instant: it is not at all a problem and perfectly workable. The typing itself is almost instant.

---

### Post by sdowney717 on 2011-05-02
how about it is a video driver issue?
I had terrible slow computer after upgrade.
To fix, I did a fresh install after backing up /home.
Now it is just as fast as when running 10.10

Also, perhaps need to install unity2d if the hardware is old.

---

### Post by aeronutt on 2011-05-02
THanks for the responses. It's new hardware (Intel i3, etc).  All the other graphics work fine.

---

### Post by benjamimgois on 2011-05-03
> **aeronutt said:**
> I'm having problems with Natty, my Dell Vostro 3550, and graphics. Lot's of trial and error to get to where I'm at, but I'm crawling towards a solution. Here's my current state:

Hardware:
Dell Vostro 3550, Intel i3 with integrated graphics, and AMD Radeon discrete graphics (HD 6630M).

Software:
Ubuntu 11.04 64bit, up to date, no significant s/w or settings changes other than described below. (So far, I've experienced the same problems on both 32 or 64 bit.)

I've been playing around with grub boot options, with the following odd results:

BOOT OPTION.................GRAPHICS BENCHMARK...........MONITOR
<as installed from CD>......------system won't reliably boot----
radeon.modeset=0............12-14 seconds....................recognized
i915.modeset=1................12-14 seconds...................not-recognized
radeon.modeset=1............5-6 seconds......................not-recognized

In short, from the benchmark results, I'm not sure the Intel integrated graphics is working at all, and I can get the radeon graphics working, but the monitor isn't recognized and has wrong resolution.

Ideas?

Would love to figure all this out as a learning experience, and to help others with similar problems.

I have the same problem my HP dv4 2080br, it has an Core I5 Intel graphics and Radeon 4550. It use to work fine on maverick but the majority of times it doesn't boot on natty. I spend the last days trying to figure how to make it work, and right now the best thing i could do was to update the intel driver to 2.15 version (last one) and also upgrade my kernel to 2.6.39rc5. System has booted on my last 3 tries. Let's see if it stays.

---

### Post by aeronutt on 2011-05-03
Please keep me informed if your upgraded driver and kernel gives you reliable, and good graphics performance. Thanks!

Have you tried using vga_switcheroo?

---

### Post by benjamimgois on 2011-05-03
> **aeronutt said:**
> Please keep me informed if your upgraded driver and kernel gives you reliable, and good graphics performance. Thanks!

Have you tried using vga_switcheroo?

Yes i confirm ! Since i update the driver and the kernel my system is a lot more stable and boot hasn't failed any time.

PPA for intel 2.15
[http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu)

Latest 2.6.39 kernel (64bits)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-05-03-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-05-03-oneiric/)

that's it. See if it work for you too.

About vga_switcheero, i'm the developper of UCC (ubuntu control center) and vga_switcheero have work ok for me until now.

---

### Post by nosushi4you on 2011-05-04
> **benjamimgois said:**
> Yes i confirm ! Since i update the driver and the kernel my system is a lot more stable and boot hasn't failed any time.

PPA for intel 2.15
[http://ppa.launchpad.net/glasen/intel-driver/ubuntu](http://ppa.launchpad.net/glasen/intel-driver/ubuntu)

Latest 2.6.39 kernel (64bits)
[http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-05-03-oneiric/](http://kernel.ubuntu.com/~kernel-ppa/mainline/daily/2011-05-03-oneiric/)

that's it. See if it work for you too.

About vga_switcheero, i'm the developper of UCC (ubuntu control center) and vga_switcheero have work ok for me until now.

Could you please explain to me how to do this? I'm having a similar problem with my switchable graphics cards, and I would love to update the intel driver as it works well with Unity when I can get the system to boot.

---

### Post by aeronutt on 2011-05-04
To get to reliable boot using only the integrated Intel graphics, I responded in another thread, hope this helps.

[http://ubuntuforums.org/showthread.php?p=10767242#post10767242](http://ubuntuforums.org/showthread.php?p=10767242#post10767242)

I personally haven't tried vga_switcheroo yet. Or, the new AMD PowerXpress, which is supposed to allow switching using the propriety AMD driver (vga_switcheroo uses the slower open driver). ([http://www.phoronix.com/scan.php?page=news_item&px=OTM4Ng](http://www.phoronix.com/scan.php?page=news_item&px=OTM4Ng))

---

### Post by prabhakar.9885 on 2011-10-06
> **aeronutt said:**
> THanks for the responses. It's new hardware (Intel i3, etc).  All the other graphics work fine.

I had recently bought Dell Vostro 3550(i3, integrated Graphics, pre-installed with Ubuntu 11.04).
The performance is really good.

But, I am not able to enable the Desktop effects in Ubuntu.
I re-installed the Ubuntu. still, not able to enable the Desktop effects.


Any suggestions?

---

