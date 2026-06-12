---
title: "Change of motherboard = sound borked"
date: 2005-05-15
forum: Desktop Environments
---

### Post by Wardhog on 2005-05-15
My Asus A7N8X-X motherboard went boom last week, so I've had to go and get a new motherboard.  Unfortunately, no one seems to have the A7N8X-X any more, so I had to get a different one (Abit K7V-V).  
I was extremely pleased with the way Ubuntu accepted this change of hardware with good cheer (NIC supported without a problem), but I noticed two standout problems.
Video and sound.
Video is fine now, a quick dpkg-reconfigure xserver-xorg saw me right.  However, I don't know if I can do an equivalent for the onboard sound chip.  I don't know which package to dpkg-reconfigure to get my sound working.

An lsmod shows that SOMETHING has been loaded, but I still get no sound.  Can anyone tell me how to tell Ubuntu to rediscover the sound devices?

---

