---
title: "Drivers for PCI Wireless Adapter (TP-Link WN353G)"
date: 2009-01-17
forum: General Help
---

### Post by UranUtan on 2009-01-17
Hi,

Using Ubuntu 8.10.

Any of you have successfully installed the driver of the PCI Wireless adapter, Brand: TP-Link, Model WN353G.

If so can you please share your experience? Or if you know the technical steps, I would appreciate some pointers.

Thanks in advance.

---

### Post by mrund on 2009-01-18
Yeah, I did it last night in five minutes thanks to a tip from user **brons2**. Remarkably simple!

Using Synaptic, I downloaded and installed ndisgtk, ndiswrapper-common and ndiswrapper-utils-1.9.

Ndisgtk installs a GUI utility under the Administration menu called Windows Wireless Networks. Using the mini-CD delivered with the card, I pointed the program at the Windows 98 driver. Then it worked!

---

### Post by UranUtan on 2009-01-18
Super cool, Thanks for the tips. Going to try now.

So ndiswrapper is something that executes a Windows driver? Is it considered "good practice" for doing so?

---

### Post by steeleyuk on 2009-01-18
Its preferable to have native Linux drivers, especially for problem solving. Using Ndiswrapper also introduces another thing that you have to consider if theres a problem. 

That being said, alot of people use it successfully and if people can't/won't pay for a natively supported wireless card then its about the only other option.

---

### Post by UranUtan on 2009-01-20
Update:

Read in other posts that the Atheros chip is recognized by Ubuntu. The TP-Link wireless PCI adapter TL-651G is just $7 more expensive. Fortunately it has the Atheros chip.

And indeed, the TL-651G is recognized automatically. So basically, changing the hardware fixed the issue. Not a very geeky solution, but it's simpler for me.

---

### Post by ValentineX on 2011-08-20
I had the same problem with Linux mint, Ubuntu all the time.

How to solve the problem:

using ndiswrapper utility install WN353G driver for windows 98 or windows ME

Then attach your WN353G wireless lan card. It will work fine without any problem :popcorn:

---

