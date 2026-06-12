---
title: "BCM 4318 on a Presario V5000 with Jaunty"
date: 2009-05-26
forum: General Help
---

### Post by Sentience on 2009-05-26
I know this can work, because it worked for me before. I dont know what happened. I reinstalled and now I cant figure out how I got it to work last time.

The bad news is that I got this message...

 lspci | grep Broadcom\ Corporation
06:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

Supposedly this is the difficult situation when you get that message.

However, I KNOW this can work because Ive done it before. This is an internal wireless card, so it didnt come with its own disk for using the windows driver. I would have no idea how to extract just that driver, and I dont believe that on this particular laptop I left a partition to swap files. 

I would like to use the native driver. It looks like its recognized but turned permanently off. What do I do?

I know this question has come up before, but tat was on previous releases and its hard to navigate all the threads that give you a different answer depending on what info comes back based on that command line I posted on top.

---

### Post by Sentience on 2009-05-26
Ok. I followed some of the other instructions, installed b43, and all I had to do was restart my computer to get it to work.

---

