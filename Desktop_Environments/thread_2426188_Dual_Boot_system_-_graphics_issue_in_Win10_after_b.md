---
title: "Dual Boot system - graphics issue in Win10 after booting in Ubuntu 19.04 - X1 carbon6"
date: 2019-09-05
forum: Desktop Environments
---

### Post by ju-es on 2019-09-05
Hi community,
I have a rather special problem, for which I would very much appreciate any expert input:
The setup:
I'm running a** GRUB2 dual boot system of Win10 and Ubuntu 19.04** on a **lenovo X1 carbon 6th** generation (Intel UHD graphics).
Things are working fine when booting into Win10 and working there. And similarly, things work fine when booting into Ubuntu 19.04 and working there (despite a number of posts of other people complaining about problems with Ubuntu on the X1 6th; I guess most of them just got fixed over time; I didn't put any special effort into fixing bugs). I haven't really benchmarked battery life or performance, but that's besides the point for this post.

The problem:
When I'm **booting into Ubuntu, shut down and reboot into Win10**, it looks fine at first sight. But **within a minute or two,** the laptop** screen starts to very slowly become black on the corners**. Then you start noticing that it looks more pixely than normal. There is also a **more and more pronounced 'retention' of graphics on the screen** (means you can still see what was displayed before on top of what is displayed now; i.e. it is not updating correctly). There is also a bit of a darkish violet shade to everything. And over a few minutes these effects become so strong, that the laptop monitor is all but unusable. When a **secondary monitor** is attached, that **image is fine and not affected**. 
And now it starts to become really strange and relevant for this Ubuntu forum:** If I restart the laptop, you can already see a flickering of the screen when the lenovo BIOS startup screen **comes up and through GRUB etc. You can actually see whatever was displayed before shutting down (last email you read before or such), while waiting for Win10 or Ubuntu to start up. Even though the laptop was shut down and the display blacked out before. If I **boot into Ubuntu**, the screen **problem persists there**. If I **boot into Win10, the screen problem persists** there.
Clearly, this freaked me out quite a bit once it happened for the first time, but the damage is not permanent. 
I don't have a clear timeline, but usually a **few hours of not using that screen **(either secondary monitor only or just laptop off) will bring everything **perfectly back to normal.** That is a normal display under Ubuntu or a normal display under Windows10.
The problem is **absolutely reproducible**, meaning EVERY TIME I boot into Ubuntu and then after into Win10 I get the same problem. There also seems to be a time component to that, though. Boo**ting into Linux, shutting down. Waiting several hours and THEN booting into Win10 doesn't seem to affect the display at all**. However, the **time I spend in Ubuntu doesn't seem to make a difference**. Just booting to check something out in Linux for 5 min and then rebooting into Windows is enough.
The problem also is persisting since I got the laptop a few months ago until now (I happened to have more work requiring Windows than Linux recently and usually work with 2ndary display anyways, so I am grudgingly enduring it and without any idea what the cause might be, I didn't try fixing the problem so far).

All of this together seems to be a very odd combination to me. Somewhat it seems a hardware problem, because it affects both OSes once it happens, but then it is caused by a certain OS, i.e. a software. 
And I know the problem manifests actually in Win10, so why a Linux forum? But for one part, it seems to be caused by Ubuntu, then it also persists into Ubuntu once it happens and finally I trust the Linux Community to have a bit more creativity and understanding of OSes.
It almost seems to me that there is some code getting pulled over from a Linux boot into the Win10 boot through a complete shut down of the system, but I'm way out of my league there.

Anyways, I would be happy if someone with a lot more insight than me has an idea what might be happening. 
And maybe it is entertaining for you guys, too. Kind of a challenging riddle.

Thanks

Julian

---

### Post by oldfred on 2019-09-06
I remember years ago, we said one system could not cause issues on another system. User had Internet issues. It turned out his issue was that Windows was not resetting the Internet card/chip, so settings from Linux were carried over. Of course Linux was blamed and Linux had to a fix to reset chip on shutdown.

So one system cannot cause issues on another. :)

Not familiar with your issue. But a few things to start looking at.

Have you updated UEFI from vendor?
Even Intel has some updates to its Linux driver.

Do not think this is related, but I use this on my newer system.
        i915.fastboot=1 kernel parameter. Fastboot helps provide a clean, flicker-free Linux boot experience.
New 5.1 kernel will include it by default on Skylake and newer 
    
This may tell more?
        [https://wiki.archlinux.org/index.php/intel_graphics](https://wiki.archlinux.org/index.php/intel_graphics)
A list of all options along with short descriptions and default values can be generated with the following command (is a long list on my system):
$ modinfo -p i915
To check which options are currently enabled, run (had to install this first:sudo apt install sysfsutils
)
# systool -m i915 -av 

Mine for reference, but I have an Asus Haswell based motherboard.
```
fred@bionic-z97:~$ systool -m i915 -av 
Module = "i915"

  Attributes:
    coresize            = "1617920"
    initsize            = "0"
    initstate           = "live"
    refcnt              = "6"
    srcversion          = "55405D086E288D29506BF4F"
    taint               = ""
    uevent              = <store method only>

  Parameters:
    enable_hangcheck    = "Y"

  Sections:

```

Note sure if this still applies, I remember installing these but I think it was with 16.04:
[https://askubuntu.com/questions/1044226/which-intel-graphics-firmware-version-is-in-use-how-to-change-that](https://askubuntu.com/questions/1044226/which-intel-graphics-firmware-version-is-in-use-how-to-change-that)

---

