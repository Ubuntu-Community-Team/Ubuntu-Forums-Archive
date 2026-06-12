---
title: "Ubuntu 12.10 Fails to Boot on HP Pavillion dm4-3060sf"
date: 2013-01-22
forum: Desktop Environments
---

### Post by picosam on 2013-01-22
Even though the Live CD worked wonderfully, and the installation went through 100% smoothly, the laptop does not start at all after the first reboot post-installation. When I went through recovery mode from Grub, I can see that it simply stops at detecting the manufacturer of the fingerprint sensor. Is there anyway I can completely disable this device and have it continue booting?

Thanks in advance,
Sammy

---

### Post by picosam on 2013-01-26
No idea? :(

---

### Post by oldfred on 2013-01-26
Do not know about fingerprint sensors. 

I might disable it in BIOS and then see if you can boot. Then you may have to see if a driver update is available to manage the fingerprint sensor.

---

### Post by picosam on 2013-01-26
Unfortunately there's nowhere in the BIOS where I can disable it :(
If only I could just boot into the system, I can then try to disable it from within or even find a driver update... but I just can't find a way to surpass that dreadful halt.

---

### Post by oldfred on 2013-01-26
There seems to be a ppa, but I have no idea how you install. Can you boot from liveCD/DVD/Flash? Then you may be able to chroot into your install and install the reader from inside your install.

[https://launchpad.net/~fingerprint/+archive/fingerprint-gui](https://launchpad.net/~fingerprint/+archive/fingerprint-gui)

---

