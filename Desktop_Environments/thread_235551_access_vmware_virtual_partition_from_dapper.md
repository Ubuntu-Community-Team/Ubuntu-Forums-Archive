---
title: "access vmware virtual partition from dapper?"
date: 2006-08-13
forum: Desktop Environments
---

### Post by mmcmonster on 2006-08-13
Hi.
  I recently started running Windows XP under vmware server under Ubuntu Dapper.
  Unfortunately, I created a fairly large file under Windows XP that I can't seem to get out of the virtual drive (it's too big (a few gigabytes) to fit in my USB key drive or to email to myself, and my firewire external hard drive is not supported (?) by vmware). vmware doesn't want to allow me to access my physical partition unless vmware server is running as root, I believe.

  I was wondering if it was possible to access files in the vmware created partition file in the host OS.

---

### Post by evil_elman on 2006-08-13
You should be able to create a 'virtual network' between the host (your Ubuntu PC) and the virtual machine. This way, you should be able to transfer whatever file (and whatever size) you would like to between them two.

I've done it myself. If you've done the VMWare Server settings right all you have to do is to create a network share in (virtual) Windows and then go to the 'Places' menu and look under 'Network Servers'.

You should be able to find all available Windows shares under there including the one from your vitual PC on your virtual network.

---

