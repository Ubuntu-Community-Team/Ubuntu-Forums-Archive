---
title: "No sound and low FPS.."
date: 2006-07-30
forum: Gaming &amp; Leisure
---

### Post by SephirothXIIIX on 2006-07-30
I followed the directions located here, so I could play World of Warcraft in Ubuntu..

[https://wiki.ubuntu.com/WorldofWarcraft](https://wiki.ubuntu.com/WorldofWarcraft)

It worked well, except.. My frames per second are pretty low (10-20), compared to what I normally get in WoW (40-50)..

I copied the WoW folder from my NTFS drive, so I do not believe video options inside of *WoW* are the problem, because I used to get a higher FPS with the same settings, in Windows..

I also do not have sound..

Any suggestions on how to fix this problem would be greatly appreciated.. :D

---

### Post by SephirothXIIIX on 2006-07-31
*bump*

---

### Post by ash211 on 2006-07-31
So the WoW folder is on a linux drive now?  NTFS seems slower than ext3 on my machine, so you might want to make sure it's not on an NTFS drive.

---

### Post by SephirothXIIIX on 2006-07-31
It is on an ext3 drive..

---

### Post by ash211 on 2006-07-31
I'm not sure, since I don't play WoW.  You should try chatting with wine support at [http://www.winehq.com/site/irc](http://www.winehq.com/site/irc)

Have you run winecfg to configure sound?  I bet you'll be able to get the sound working but the FPS will be much harder to work on.

---

### Post by SephirothXIIIX on 2006-08-01
Yeah, I ran winecfg before I ran WoW (and set Wine to use OSS), and that did nothing. But, I have fixed the sound now.. My sound did not work in multiple programs, but, I fixed it. I noticed that Linux gave me the option of using my onboard sound card, and that it would sometimes default to that (it defaulted to it after I installed Ubuntu, too). So, I disabled that card in my BIOS, and now my soud works..

As for the FPS, it's still low.

---

### Post by SephirothXIIIX on 2006-08-06
*bump*

---

### Post by ash211 on 2006-08-07
All I can say is make sure you have the latest version of wine (0.9.18) and report some of your specs to the great people over at [www.winehq.com](www.winehq.com)

---

