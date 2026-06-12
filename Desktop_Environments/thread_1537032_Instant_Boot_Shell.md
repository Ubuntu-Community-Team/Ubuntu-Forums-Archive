---
title: "Instant Boot Shell"
date: 2010-07-23
forum: Desktop Environments
---

### Post by CyberXZT on 2010-07-23
Hello everyone. I refurbished a netbook and decided to put Ubuntu on it. Basically, what I would like to do is add a second entry into Grub2. I would like this entry to ONLY start a shell in ubuntu. I dont want it to start anything but a shell. I want it to start up as fast as possible and to not initialize anything unnecessary. No GUI, no network, nothing.

Basically, the idea is that during the middle of the night I typically have random notes that I want to type down, so I want to be able to turn on my netbook, hit the second grub option, and nano a note all in under a minute.

Hopefully that explains it, so what would be the best way of going at this? Is their a way to use my current ubuntu setup or?

---

### Post by staf0048 on 2010-07-23
Ok, well I don't know about ubuntu, but you could install Gentoo as your second option and just forget about adding support for all that other stuff you don't want.  You will have to add nano though (not sure if it comes with an editor by default, like vi) so you'd want to download the source for nano on the Ubuntu side, then compile it on the gentoo side.

From what I can see this is the best way to get what you want done, but may not be all that easy.

***Note - this would also involve compiling your own kernel which will dramatically increase your boot speed, but requires in-depth knowledge of your specific computer.

---

### Post by CyberXZT on 2010-07-23
Okay, thanks for your reply. What I ended up doing is using the ubuntu mini netboot iso. I used it to install a minimal shell onto a separate partition. It also uses my home partition between the two copies of ubuntu. Startup times arent instant but 3 seconds isnt that bad either hehe.

Thanks.

---

