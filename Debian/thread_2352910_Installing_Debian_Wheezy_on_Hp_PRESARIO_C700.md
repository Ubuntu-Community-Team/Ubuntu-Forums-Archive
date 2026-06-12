---
title: "Installing Debian Wheezy on Hp PRESARIO C700"
date: 2017-02-16
forum: Debian
---

### Post by fishdog on 2017-02-16
Hi, I just need a bit of advice on installing Debian Wheezy on Hp PRESARIO C700.
I'm installing Wheezy because I want to install AIRTIME, which recommends Wheezy.

I'm going to install from USB, should I use amd64 arm64 armel or armhf ?

Any other advice?

Ta.

---

### Post by wildmanne39 on 2017-02-16
*Thread moved to **Debian**.*

---

### Post by arochester on 2017-02-17
amd64

---

### Post by fishdog on 2017-02-18
Thanks!

---

### Post by gordintoronto on 2017-02-20
If this 9-year-old computer has the minimum specs, it will not provide a good experience.  Try running a Live DVD of Lubuntu to see if it even runs. The machine probably won't run Wheezy at all.

Ubuntu Server might run, but it is a command-line system, and it appears that you would face a steep learning curve.

If Lubuntu works, you should be able to install Airtime onto it.

---

### Post by arochester on 2017-02-20
> If this 9-year-old computer has the minimum specs, Oooh. My laptop is 9 years old!!!

Increase the amount of RAM if possible. 

Follow most of the instructions here: [https://www.maketecheasier.com/build-lightweight-linux-for-low-end-laptop](https://www.maketecheasier.com/build-lightweight-linux-for-low-end-laptop)

Use a NetInstall.

Uncheck everything in Software Selection except for Standard system utilities. And don't check Laptop as it says!

This will give to a TEXT based install only, no GUI yet.

Instead of:

apt-get install xorg sudo iceweasel pulseaudio
I personally would go for Chromium instead of Iceweasel.

Instead of installing lxde install lxde-core. It will install less cruft.

---

