---
title: "Dell E6510 can only boot in low graphics mode"
date: 2010-10-24
forum: Dell Ubuntu Support (CLOSED)
---

### Post by rosati_ on 2010-10-24
Hi,
I installed Ubuntu 10.10 desktop onto my Dell E6510 notebook, but I'm having some problems getting the graphics to work.

I have integrated intel graphics, and I can't get any sort of intel driver to boot and display on my laptop's monitor.
Only way I've gotten ubuntu to display on it is by adding "nomodeset xforcevesa" to the boot parameters.
i915.modeset=0 gets me until X starts, but then the kernel panics.

I'm able to get the intel drivers to display to an external monitor if I connect one, but my laptop monitor stays blank.

Is there a well known workaround for this problem?
I've looked around but couldn't find any simple solutions.... I'm pretty new to ubuntu and linux in general so I wouldn't know how to edit and recompile a kernel or anything like that.

Anyone know what I could do to get an intel driver working?
Playing video at 10fps with the vesa driver won't cut it forever.

Thanks.

---

### Post by P4man on 2010-10-24
It seems like your machine has both an intel IGP and an nvidia card, is that possible?
If so, try booting with

```
nouveau.modeset=0
```

If that gets you in to X, download the proprietary nvidia drivers through system > administration > additional drivers.

---

### Post by rosati_ on 2010-10-25
As far as I know I don't have an nvidia card in my laptop.
I'll try that anyway.

No, that didn't change anything. I'm 100% sure there's no nvidia card in my laptop. I still get a black screen on boot where I can hear the login sounds and use keyboard shortcuts, but not see anything.

I noticed an error that's displayed during boot before X starts (with no additional parameters, just the default)
```
[7.435693] intel ips 0000:00:1f.6: failed to get i915 symbols, graphics turbo disabled
```

Googled it, seems to do with the built-in overclock capabilities on the intel processor. Would that have anything to do with the graphics issues I'm having?


Also I've been able to get the intel drivers to display on the dell's monitor by plugging in and removing the vga cable to an external monitor. Any way to trick ubuntu into thinking I've done that every boot?

---

### Post by bach on 2010-12-05
It's a bug. See 

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/600453) 

See also 

[https://bugs.freedesktop.org/show_bug.cgi?id=29278](https://bugs.freedesktop.org/show_bug.cgi?id=29278)

---

