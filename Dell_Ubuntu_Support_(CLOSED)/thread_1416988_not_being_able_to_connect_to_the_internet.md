---
title: "not being able to connect to the internet"
date: 2010-02-26
forum: Dell Ubuntu Support (CLOSED)
---

### Post by farshad_momtaz on 2010-02-26
hello,
i installed ubuntu on my inspiron 1525 but im not able to connect to internet because it does not discover the hardware. how can i fix this?

thank you

---

### Post by coffeeaddict22 on 2010-02-27
Hi,
The way around this is to put your install disc back in, and ten go to System/Administration/Hardware Drivers; in there is an option to install the Broadcom proprietary drivers.  Choose that, and you should be away.

The problem is you haven't got the hardware drivers installed.  Dell uses broadcom drivers, and Broadcom see fit to sell hardware but copyright the software that uses it.. so you buy a brick unless they are willing to maintain it.   Linux is based on the idea that the code is available and free; if it's not, then many distributions won't install it by default.  If it's a big problem to you, try Mint Linux; they're happy to install proprietary drivers as part of the install.

It sounds a bit purist to not want proprietary drivers, but there are excellent reasons.  A few years back I bought a modem; the manufacturer had software on it that diverted you to their download page for net-nanny software about 1% of the time:evil:.  They did upgrade the firmware eventually.  Networking hardware in particular is a sitter for Orwellian techniques.

---

### Post by bobcollard on 2010-02-28
> **coffeeaddict22 said:**
> Hi,
.  If it's a big problem to you, try Mint Linux; they're happy to install proprietary drivers as part of the install.

Correction, Linux Mint does not include proprietary software, instead, like Ubuntu they offer links to it according to your hardware configuration through Hardware Drivers and it has to be downloaded from the Internet the same way.  Go to Administration/Hardware Drivers in your menu and you will find the drivers recommended for your computer in Ubuntu.

---

### Post by coffeeaddict22 on 2010-02-28
My apology.  I was under the impression Mint just added the codecs; they've got a reputation for making it easier to add the capability.  
I'd take Bob's advice :)

---

