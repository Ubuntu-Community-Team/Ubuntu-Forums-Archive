---
title: "Ubuntu and Emachines"
date: 2006-04-12
forum: Desktop Environments
---

### Post by emooney on 2006-04-12
Hello,
I'm new to the forum, Linux and Ubuntu and I'm looking forward to learning alot about Linux and Ubuntu. I bought an  [emachine]("http://www.emachines.com/products/products.html?prod=T6528") that has onboard video, audio and a networking port. I formatted the disk successfully but failed the network setup. It said that it couldn't find a network card so I thought, OK, I'll come back to that. I finished the install and it was installing the rest of the packages and it restarted. Upon restart, it said "Failed to start the X server" and through me to the command prompt.

So I'm beginning to think that the OS doesn't have drivers for the video, network and audio components that are onboard. If you think this is the case, let me know and I'll start looking down that path.

My emachine specs are above in the link and I downloaded and ran this iso:
ubuntu-5.10-install-i386.iso

---

### Post by gabruo on 2006-04-12
For the x-org problem it is probably missing the nvidia driver.  See here [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29) but that may not be much help without internet access.  Find you network card type and do a search in wiki if no other replies come.;)

---

### Post by Sef on 2006-04-12
To help narrow your search outside of Ubuntu forums, type google.com/Linux, then type in emachines.

---

### Post by aysiu on 2006-04-12
Maybe the newer versions of eMachines don't use Linux-compatible hardware?

I have a T3065 and an eTower 766id, and they both work fine with Ubuntu.

---

