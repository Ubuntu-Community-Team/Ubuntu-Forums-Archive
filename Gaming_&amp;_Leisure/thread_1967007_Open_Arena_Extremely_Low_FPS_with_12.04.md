---
title: "Open Arena Extremely Low FPS with 12.04"
date: 2012-04-27
forum: Gaming &amp; Leisure
---

### Post by Katla on 2012-04-27
I first checked out Open Arena with 11.04, but found that it was unplayable as it had a framerate of about 8. When 11.10 came out, I checked into it again, and it worked like a charm. 

Today I upgraded to 12.04 and it is worse than ever. FPS of 2 or something crazy. I can barely navigate the menu, let alone try to play it. 

So what gives? I've made no hardware or driver changes in between 11.04/11.10/12.04. I've checked my GL setting with the grep command, they're fine. As they should be, since I've made zero changes. It's something in 12.04, and I have no idea what it could be, alone how to fix it. 

Any help would be greatly appreciated. Thank you.

---

### Post by leilei on 2012-05-01
Make your way to the Driver Info page. It's found in Setup > System

Does it say "Mesa" or "Software" under the VENDOR label?


Obviously there's no acceleration with your video driver. OA generally runs at least 20fps with some prehistoric 3d hardware, so 8fps on a modern pc means it's not working at all.

---

### Post by Katla on 2012-05-05
It says "Mesa". 

I'm having trouble elsewhere with problems that seem to be related to my video driver. VLC not working properly (freezing on full screen), and the Totem Movie Player ignoring brightness/contrast controls. I've read up a bit on drivers, etc., but I am mostly confused. 

I'm using an onboard Radeon graphics card, r600 or something to that effect, 1200 series. Gallium drivers.

---

### Post by ahso4271 on 2012-05-07
Install the closed source driver from ATI! I use Nvidia and this is very easy to install... I've also heard that Nvidia is better so maybe even get a suitable Nvidia card from Ebay?

---

