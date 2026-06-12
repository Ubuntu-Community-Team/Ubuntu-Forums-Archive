---
title: "BCLK OC Problems"
date: 2017-06-09
forum: Gaming &amp; Leisure
---

### Post by k1tt3hk4t on 2017-06-09
Halloa! I've been trying out [Ubuntu Budgie]("https://ubuntubudgie.org/"), which runs on Ubuntu 17.04 "Zesty". It's all run smoothly so far, but attempting to do a CPU BCLK (Base Clock) OC (Overclock) has led to crashes at boot-up. I have changed my GRUB settings to lock the CPU C-state to 0. I'm using an i3-6100 [(Yes, no "K" at the end; BCLK OC doesn't require this.)]("https://www.youtube.com/watch?v=gfiGJCUANbA") with an ASRock Z170X-UD3 motherboard. Under the overclock, I've set the BCLK such that the RAM frequency is kept stock and have disabled any power saving features I can find, as well as the thermal monitoring and iGPU to make sure the overclock doesn't crash on startup.

After the GRUB modifications (Setting intel_idle.max_cstate=0, as reccomended [here]("https://www.phoronix.com/forums/forum/hardware/processors-memory/848450-bclk-overclocking-on-z170-skylake-chipsets-prevents-ubuntu-from-booting") on Phoronix) my boot screen is [this]("http://i.imgur.com/PB6tg2e.jpg") without the overclock and [this]("http://i.imgur.com/e4KbLwB.jpg") with it. On the latter screen, it freezes and *does not* proceed to ask for my decryption key.

However, this same overclocking setup with the GRUB tweak ran fine on Linux Mint (which runs on Ubuntu 16.04); as such I believe there is no problem with the hardware and must either be the fault of Ubuntu, GRUB, or the Linux kernel itself.

If I failed to provide any info which could help me come to a solution, please let me know and I'll gladly post it here.

Thanks in advance.

---

