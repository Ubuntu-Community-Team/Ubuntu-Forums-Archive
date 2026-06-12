---
title: "How do I make my Netgear Wireless-G USB 2.0 Adapter WG111 work?"
date: 2009-03-09
forum: General Help
---

### Post by Wiggler on 2009-03-09
How is it that Ubuntu doesn't have the drivers for such devices, yet Windows Vista does?!? I want to get on the internet with Ubuntu and do this and that, in case Vista gives me trouble.

As explained in the title, my USB wireless adapter is a Netgear Wireless-G USB 2.0 Adapter WG111.

And I am a Linux newb, so please be clear on what I need to do.

---

### Post by gustavocqd on 2009-03-09
I'm afraid this is a difficult one, but not impossible netgear do not release specific drivers for linux so you'll have to try to use ndiswrapper around the windows driver:

[HTML]https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper[/HTML] 

As a rule try to verify if the hardware is supported in linux before buying. And in general stay away from netgear products.

---

### Post by Scubdup on 2009-03-09
Wiggler, I had [real problems with that netgear adaptor]("http://ubuntuforums.org/showthread.php?t=1062246&page=2"). In the end I bought a different dongle (from Edimax, who seem very happy to work with the Linux community) and haven't had any problems since. Whilst normally I'd consider that a bit of a failure (not persevering) for £12 the ease of the "solution" was worth it in my mind.

EDIT: Just to say, gustavocqd seems to be right. I did a lot of research and Netgear seem pretty problematic. Some poeple seem to sort the problem with NDISWrapper and the windows drivers but that seemed like a messy fix to me.

---

### Post by lindsay7 on 2009-03-09
I had the same problem with the netgear wg111V2, seems there are two different chipsets in the wg111v2 and from what I read one does not work and the other may with a wpa setup,

I bought Linksys WUSB54G and it works plug and play, I also read a post last week that the Belken F5D7050 also worked out of the box.

---

