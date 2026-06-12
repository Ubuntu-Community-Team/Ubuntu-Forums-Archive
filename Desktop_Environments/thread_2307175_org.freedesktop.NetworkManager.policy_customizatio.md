---
title: "org.freedesktop.NetworkManager.policy customizations lost after kernel update"
date: 2015-12-22
forum: Desktop Environments
---

### Post by blm14 on 2015-12-22
So, this is a weird one. I have a laptop running ubuntu 14.04 that is authenticating against active directory using Likewise-OPEN. The policy where i work is to not include regular users in wheel, and instead give them sudo access to specific commands in SUDOERs...

For a long time I could not get my user on this laptop to be able to change the default wireless SID, until I found this:

[http://askubuntu.com/questions/244567/remove-sudo-password-when-connecting-to-new-wifi-network](http://askubuntu.com/questions/244567/remove-sudo-password-when-connecting-to-new-wifi-network)

The suggestion of changing the relevant line in org.freedesktop.NetworkManager.policy permits my user to be able to switch wireless SIDs, yay!

But the strange part is that any time I either install a new Kernel, or do an apt-get autoremove to expunge old kernels (the system is full disk-encrypted using LVM/Luks, so the boot partition is small) the change is reverted and I can't switch SID's again. I wouldn't have a clue where to submit this as a bug - Kernel? Apt? Grub? - so am starting here.

---

