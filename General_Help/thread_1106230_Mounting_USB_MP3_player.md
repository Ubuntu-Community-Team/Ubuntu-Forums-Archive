---
title: "Mounting USB MP3 player"
date: 2009-03-25
forum: General Help
---

### Post by KCG102282 on 2009-03-25
How do you mount a MP3 player from the command line if it doesn't show up in nautilus?

---

### Post by evilaim on 2009-03-25
Well, lets try and gain a bit more information, as there has to be thousands of MP3 players.

Lets start with a few basic details

-What version of Ubuntu are you using?
-What MP3 player is it?

Just in case I miss this thread, You'd be best to search on google for "Ubuntu+your MP3 model".  Usually doing so will help you obtain a walk through.

If you're talking about an IPOD or ZUNE, you'd have to get black market software for such a thing.

---

### Post by KCG102282 on 2009-03-25
I am running Ubuntu 9.04 Alpha 6. I have already mad a bug report saying that it doesnt automatically connect. I have a sandsdisk sansa e250. I have switched it to MSC mode. I does connect in Debian. All I need is a way to mount it manually.

---

### Post by evilaim on 2009-03-25
sudo mount -t vfat /dev/[device] /mnt/point

I'm not sure what the device name would be.

---

