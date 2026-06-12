---
title: "Problems with wireless on a Dell XPS M1330"
date: 2013-02-14
forum: Dell Ubuntu Support (CLOSED)
---

### Post by Inoki on 2013-02-14
Hi all,

on behalf of my friend I would kindly ask for your help and support.

She is a linux newbie, impressed by linux very much, especially Ubuntu and its philosophy, like me.

The only problem is her lappie is a bit old and not really supported.

She wanted to install Ubuntu 12.04.1 LTS, but the same occured with 12.10 x32 bit. *We are now testing Ubuntu 12.10 x32 bit and ethernet works, we need wireless to work.*

Her specs:

**Name:** Dell XPS M1330
**Processor:** Intel Core Duo T7100 1.8Ghz
**Screen:** 13.3&#8221; WXGA
**RAM:** 4GB
**HDD:** 250GB
**Optical Drive:** DVD+-RW
**Graphics:** Nvidia GeForce 8400M GS
**Network:** 10/100 Ethernet + Intel 4965AGN 802.11abgn Wireless
**Other:**	2 x USB2.0, 1 x Firewire

Info taken from [this link]("http://www.linlap.com/dell_xps_m1330").

What would you have us do?

Try this:

```
sudo apt-get remove bcmwl-kernel-source
sudo apt-get install firmware-b43-installer b43-fwcutter
```

or

```
sudo modprobe -r b43 ssb wl
sudo apt-get remove bcmwl-kernel-source 
sudo apt-get install build-essential dkms linux-headers-generic
sudo apt-get install bcmwl-kernel-source
```

or

```
lspci

sudo lshw -C network

lsmod | grep -e b43 -e wl
```

first.

---

### Post by Inoki on 2013-02-14
Do you guys believe this might resolve the issue, since ethernet is working?

[IMG]http://i47.tinypic.com/xfvofl.png[/IMG]

If so, should we install the **legacy** option, or **the first one**, **or both** if possible?

---

### Post by Inoki on 2013-02-14
Ok guys, we managed to get it to work.

**Ubuntu is awesome!**

The problem was, that on the LiveUSB / DVD the wireless was disabled by default. Please enable it.

Thank you for this great operating system!

---

