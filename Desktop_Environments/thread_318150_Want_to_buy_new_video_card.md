---
title: "Want to buy new video card"
date: 2006-12-13
forum: Desktop Environments
---

### Post by bsalt on 2006-12-13
Hey guys, I am currently using an onboard video card - the infamous Intel 945 GPU - and I want to upgrade in the near future to an Ati or Nvidia card. I have never actually changed out my physical hardware after installing Ubuntu, and I am wondering if there is a way I can install this video card without having to re-install Ubuntu. 

I am still sort of new in the hardware department and would also like to know if it is possible to keep both video cards enabled in Ubuntu, and if possible, tell Ubuntu that I want to use the new card as the primary video card.

Is this possible, or am I shooting too high?

Thanks guys,
Jon

---

### Post by taurus on 2006-12-13
I recommend you get nVidia card instead of an ATI graphic card.  Then, you need to go into the BIOS to turn off the onboard video card.  Then, boot Ubuntu into recovery mode from GRUB menu and at the prompt, reconfigure your X again to use the graphic card...

```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by bsalt on 2006-12-13
> **taurus said:**
> Then, you need to go into the BIOS to turn off the onboard video card.

Well, I'd like to keep the onboard video as a secondary GPU for a second display. Is that possible?

---

### Post by tmilam on 2006-12-13
You're best bet is maybe getting an nvidia card with either dual dvi or dvi + vga. You can pick these up on the cheap and get a significant performance boost. 

Here's a little story:

I had a 256 MB ATI Radeon 9550 AGP 8x card. It ran well in windows but poorly in linux. Hard-locks (computer completely froze) became common place when using the proprietary drivers. 

I sold this card on ebay for $50. To replace it I got an nvidia video card that cost me $15 + shipping (Nvidia Quadro XGL 700 AGP 4x w/ 64mb ram). My 3d performance has literally doubled.

So what does that tell you about the state of proprietary drivers between ati and nvidia?

---

### Post by bsalt on 2006-12-13
Well, then I think I'm set for an Nvidia card - now I just have to find one. I'm thinking about going with a Gefore 7 series card for OpenGL2.0 support.

---

### Post by drphilngood on 2006-12-13
> **bsalt said:**
> Well, then I think I'm set for an Nvidia card - now I just have to find one. I'm thinking about going with a Gefore 7 series card for OpenGL2.0 support.

The Geforce 7900GS is a really good buy.  You can pick up one for under $200, now.

---

### Post by chrisccoulson on 2006-12-14
I'm running a 7900GT here, with no problems. Although, I haven't tried running 2 monitors with it yet.

---

