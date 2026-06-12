---
title: "Wireless connection"
date: 2007-12-28
forum: Dell  Ubuntu Support
---

### Post by mehran5 on 2007-12-28
Hi. I am very new to Ubuntu. I just installed 7.10 on Dell Latitute D620 with the wireless device Intel PRO/Wireless 3945AGB. It lists the device when I run "sudo lshw -C network." It does not list the device when I run iwconfig. The response to iwconfig is:

lo         no wireless extension
eth0    no wireless extension

I think my device is not on, but I am not sure. Can anybody help?

Thanks.

---

### Post by buntunub on 2007-12-28
You can try [this]("http://ubuntuforums.org/showthread.php?t=541134&highlight=3945AGB")

Best bet is to run a search for your chipset on these forums and on google. Its a little bit of work but well worth the effort in the end when you get it all up and running with some newfound knowledge to boot.

---

### Post by woodcarver on 2007-12-29
Another thing to think about trying is a PCMCI wireless card. Dell on-board wireless can cause problems. I've found the best thing is to disable it in the BIOS and get a card.

---

