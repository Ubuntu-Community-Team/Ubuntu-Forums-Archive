---
title: "Elden Ring performance drop since updating to 24.04"
date: 2024-11-25
forum: Gaming &amp; Leisure
---

### Post by arthurp on 2024-11-25
Hey y'all lovely people,

I upgraded to 24.04 from 23.10 and I am seeing a 20% drop in FPS in Elden Ring since then (~60 to ~50 and as low as 45). I've been trying to figure out why, but I haven't been able to find any real clues though I can rule some things out. My suspicion is that this is a CPU issue in some way. Elden Ring isn't super well optimized on the CPU side and my CPU is at the bottom of the range for it. However, it was reliably 60fps before the upgrade.

Has anyone experienced anything like this? Can anyone recommend anything to try?

There are definitely more things I could try, but I thought I would ask first because doing more OS installs and such like seems silly if this is a known issue or someone has easy things to try first.

Thanks! I'm super curious to hear what people think might be going on even if we can't solve it. OSs are interesting beasts.

**Now a mess of details**

The system is:

* AMD Ryzen 7 3800X
* 32GB RAM
* Nvidia 4080 SUPER with Nvidia divers 550.
* Kubuntu 24.04 (up to date as of 11/25/24)
* Steam Proton 9.0 (also tested with experimental)
* Xorg

I was able to find this: [https://discourse.ubuntu.com/t/24-04-considerably-slower-than-20-04-or-22-04-for-some-high-system-percentage-usage-cases/41987](https://discourse.ubuntu.com/t/24-04-considerably-slower-than-20-04-or-22-04-for-some-high-system-percentage-usage-cases/41987), but using a pre-6.6 kernel as mentioned there doesn't help.

I have ruled out some things, as best I know how:

* Not GPU issue or GPU communication/PCIe issue. I am on a 4080 and reducing the quality, including texture resolution doesn't make any measurable difference.
* Not a kernel issue. I tested again using the original kernel left over from before the upgrade (6.5.0-44-generic) and on the 24.04 kernel (6.8.0-49-generic).
* Not a CPU throttling issue. The CPUs are scaling up including going to their boost clock.
* Not a Proton issue. I did not change that during the upgrade and I tested on 9.0 and experimental.
* Not a game issue. The game did not update that I know of.
* Not a CPU load issue. The CPU is relatively unloaded and the game only uses ~4.5 CPUs worth of time and there are 8 available.

There are definitely things I could do.

* I have not reinstalled 23.10 (or more realistically 22.04 due to still being supported) to verify that the difference is reproducable.
* I have not built mainline kernels (though this seems unlikely to help given the above).
* I have not tried any kernel command-line parameters. I wouldn't really know what to try.
* I have not tested a range of nvidia drivers since I'm pretty sure I didn't upgrade that.

I did try Wayland, but I don't really think it's better by eye and neither of the FPS displays I had used worked so I can't measure (I tried the DXVK, nvidia, and steam ones). I would rather not use Wayland because of reliability issues, especially around the Nvidia drivers.

---

