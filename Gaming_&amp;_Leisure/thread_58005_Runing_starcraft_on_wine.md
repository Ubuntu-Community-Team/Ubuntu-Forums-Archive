---
title: "Runing starcraft on wine"
date: 2005-08-18
forum: Gaming &amp; Leisure
---

### Post by bobmaster on 2005-08-18
I was surprised but starcraft works great with wine. I just have one problem the sound doesn't work. It works on the install but when I play the game theres no sound.

---

### Post by jumanji on 2005-08-18
Are you useing latest Wine (20050725)?

If Yes.. use the "winecfg" command in a Terminal window and config sound as "Emulation" from there..

---

### Post by gorkhal on 2005-08-19
[QUOTE=bobmaster]I was surprised but starcraft works great with wine. I just have one problem the sound doesn't work. It works on the install but when I play the game theres no sound.[/QUOTE]

try killing esd, that might work

$killall esd 

then run starcraft. 

Just a question though, how fast does it run?? On my machine, wine starcraft ends up using 80-90% of the processor, and still runs a bit jerky. I am using the new wine builds as well.

---

### Post by bobmaster on 2005-08-29
It runs just as fast as window or mac. :grin: And thank you for the reply.

---

