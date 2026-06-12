---
title: "Wireless connection one-time-only?"
date: 2005-10-14
forum: Desktop Environments
---

### Post by johnkennethhughes on 2005-10-14
I've installed Ubuntu 5.10 on my laptop and set up a Belkin (Broadcom) wireless card using the ndiswrapper-utils as per instructions for 5.04 given by jonny in the forums ([http://ubuntuforums.org/showthread.php?t=25683](http://ubuntuforums.org/showthread.php?t=25683)) - very quick and easy. Everything works fine until I reboot the computer and suddenly I'm no longer able to access the internet. Nothing seems to have changed about ndiswrapper-utils, bcmwl5 or the wireless settings System->Administration->Networking and the power light on the wireless card itself stays on. But I can't access the internet.

Removing everything and starting again (reinstalling ndiswrapper-utils and reconfiguring everything) makes it work again - but only until the next time I power down. Am I missing something obvious here?

---

### Post by audax321 on 2005-10-14
Okay, I've never used ndiswrapper or dealt with that specific wireless card. But, it seems like something might be wrong with your /etc/network/interfaces file that is preventing the card from properly configuring itself on the next boot. Please post it and maybe someone will notice something.

---

### Post by jimmyp on 2005-10-14
after you setup ndiswrapper and have it working do
sudo ndiswrapper -m

if that doesn't make it work on boot then try doing a
sudo modprobe ndiswrapper

you don't have to set everything up again, just load the module

---

