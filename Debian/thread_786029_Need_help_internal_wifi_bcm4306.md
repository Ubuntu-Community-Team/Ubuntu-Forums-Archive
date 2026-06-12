---
title: "Need help internal wifi bcm4306"
date: 2008-05-07
forum: Debian
---

### Post by NautTboy on 2008-05-07
I have an old thinkpad with 433mhz.  I have an internal wifi card (mini-PCI) made by Broadcom. lpci show it's broadcom bcm4306.  How can I install this card without having to get online.  This old laptop does not have LAN port.

---

### Post by agim on 2008-05-07
install ndiswrapper-common and ndiswrapper-utils-1.9 from the livecd (I think is should be there).

Use ndiswrapper to install your wireless driver, here is a good how-to for that.

 [http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom+4312](http://ubuntuforums.org/showthread.php?t=766560&highlight=Broadcom+4312)

---

### Post by NautTboy on 2008-05-08
Yea a good how to, but you need internet.  What i need help on is to get on the internet.

Which one comes first, the eggs or the chicken?

---

### Post by p_quarles on 2008-05-08
Since Debian doesn't distribute live CDs, I don't think that will work. If you have the full Debian CD/DVD set, you should be able to find NDISwrapper on one of those. I'm fairly certain that it's not on the net install disk.

You'll have to download the Windows driver for the card using another computer, and then use some kind of storage medium to transfer it to the laptop.

---

