---
title: "WiFi Achilles Heel"
date: 2010-05-02
forum: Desktop Environments
---

### Post by Geffers on 2010-05-02
I've been using Ubuntu for a few years now and in general am very pleased with it; it's Achilles Heel is however WiFi.

My daughter has an older HP laptop with built in Broadcom wifi, Lucid did not recognise this, neither did it recognise a Netgear PCI card or a Netgear USB adapter.

Network manager showes wifi greyed out.

lspci -vnn shows BCM4303 802.11b [14E4:4301] (rev 02)
lshw shows *-network:1 UNCLAIMED and shows product as BCM4303 802.11b wireless LAN controller.

Wifi is the most popular connection method for the average user, until it is made simpler to resolve problems a lot of potential Linux users 
will be put off :mad:

Geffers

---

### Post by John Bean on 2010-05-02
For what appears to be dogmatic OSS-only reasons the install CD has no restricted drivers available. IMO this is nonsensical for exactly the reasons you stated and so easy to put right, all it needs is a bit of common sense and pragmatism.

---

### Post by Geffers on 2010-05-02
> **John Bean said:**
> For what appears to be dogmatic OSS-only reasons the install CD has no restricted drivers available. IMO this is nonsensical for exactly the reasons you stated and so easy to put right, all it needs is a bit of common sense and pragmatism.

I did forget to mention in my original post that the installation did detect legacy drivers for the broadcom but after installation wireless was still greyed out on network manager.

Geffers

---

### Post by John Bean on 2010-05-02
> **Geffers said:**
> I did forget to mention in my original post that the installation did detect legacy drivers for the broadcom but after installation wireless was still greyed out on network manager.

Yes, mine claimed it had "found" drivers too, but it did nothing useful when I activated them. I suspect it's just a dummy installer on the CD; lots of others have reported similar experiences.

---

