---
title: "Power Setting issue or Application problem?"
date: 2014-08-29
forum: Desktop Environments
---

### Post by pcar916 on 2014-08-29
I've upgraded to 64-bit 14.04 a few days ago. Since the installation is so new, I was unsure about whether or not to  put this question here or in Installations and Upgrades. But here seems to make sense somehow.  The upgrade has been seamless except for a couple of operator errors and trivial stumbles.  But there is one persistent thing now that never happened before.

Anytime I watch online video in Firefox, like YouTube seminars that last more than 5 minutes, and full screen or not. Unity will automatically darken the screen and Log Out this happens even when I move the curser around. It doesn't happen with the customized Netflix version of Firefox. Very annoying. Before anyone asks, the "Power" setting in System Settings is to "Don't Suspend", which is the only place I've seen to control this behavior. Now...

1. Firefox is the only application so far that does this.
2. I didn't install any other browsers and won't until after I get some feedback from this thread.
3. I've watched other (local) videos with VLC Player successfully.
4. This never happened on 12.04 LTS.
5. It's almost as if Firefox isn't transmitting a "keep-alive" signal to Ubuntu during playback.

Hardware:
AMD FX-6100 cpu
8 GiB RAM
Gallium 0.4 on AMD RS780 (on the mobo, not a discrete GPU)
Can't imagine that it matters but: Win 7 / dual-boot on a separate drive.

Ideas on where to begin?

Thanks in advance.

---

### Post by LinuXoDus on 2014-10-17
Hi picar916,

I am having some very similar problems (also on Ubuntu 14.04 x64, but Intel mobile GPU). I am suffering also while using VLC from this. Have you been able to fix this in the mean time?

BTW, these are my current graphic driver settings:
```
sudo lshw -numeric -C display
  *-display               
       description: VGA compatible controller
       product: Haswell-ULT Integrated Graphics Controller [8086:A16]
       vendor: Intel Corporation [8086]
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 0b
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:60 memory:f0000000-f03fffff memory:e0000000-efffffff ioport:3000(size=64)

```

as well as the available cpu:
```
cat /proc/cpuinfo
     ...
     Intel(R) Core(TM) i7-4600U CPU @ 2.10GHz
     ...
```

maybe someone is able to to help us figuring this out.

---

