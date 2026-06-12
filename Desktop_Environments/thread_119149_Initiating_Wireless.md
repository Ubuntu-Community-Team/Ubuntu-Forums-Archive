---
title: "Initiating Wireless"
date: 2006-01-18
forum: Desktop Environments
---

### Post by icarius on 2006-01-18
I finally got my wireless working using the NDISWRAPPER, however when I turn my comp back on, my computer sees the wireless driver installed and sees the card using NDIS, however the network settings doesn't see it and I have to reinstall it everytime. Any ideas?

---

### Post by Shadyman on 2006-01-18
You might need to edit your /etc/network/interfaces file :KS 

See: [http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Running_at_Startup:]("http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Running_at_Startup:")

---

### Post by flosofl on 2006-01-19
What chipset are you using?

I only ask because my card (HWP54G) is an ACX110. I couldn't the firmware working correctly with it, so I decided to use ndiswrapper instead. It was loading the acx module before ndiswrapper. I found I had to remove the acx kernel module from /lib/modules (be sure to **depmod -a** after) and reboot (I couldn't rmmod the acx module). Then I used ndisgtk to set up the driver and had no problems.


EDIT:  Oh yeah, every time you upgrade the kernel using apt, you'll need to remove the offending module before you reboot.  Unless you roll your own kernel.

---

