---
title: "Only slow when runnig a software, why???"
date: 2009-03-30
forum: General Help
---

### Post by group256 on 2009-03-30
Hi everyone,

I'm using ubuntu 8.10 at the moment on a fairly old sony laptop. This machine works fast enough on windows as well as ubuntu.(After turning off all visual effects). But it really starts to bug me when I start using a software, as simple as a web browser. No matter I use Firefox, Opera or Galeon, still the respons time is really really slow. I scroll down a page and I have to wait for few seconds to see the result.

But that's not all; let's say I use OpenOffice. I click on a text to edit it and takes more than 5 seconds(at least) to activate the text. While I have fast response on browsing my hard disk or menus on ubuntu. 

By the way, it's really not possible for me to watch anything on youtube full window. It's really really slow. 

Please let me know if anyone knows the answer, as I really love to use ubuntu, but this problem is really bothering me.

Thanks.

---

### Post by Yashiro on 2009-03-30
List the exact name of the laptop and it's video chip.
It sounds like you dont have video set up properly.

---

### Post by DGortze380 on 2009-03-30
> **group256 said:**
> Hi everyone,

I'm using ubuntu 8.10 at the moment on a fairly old sony laptop. This machine works fast enough on windows as well as ubuntu.(After turning off all visual effects). But it really starts to bug me when I start using a software, as simple as a web browser. No matter I use Firefox, Opera or Galeon, still the respons time is really really slow. I scroll down a page and I have to wait for few seconds to see the result.

But that's not all; let's say I use OpenOffice. I click on a text to edit it and takes more than 5 seconds(at least) to activate the text. While I have fast response on browsing my hard disk or menus on ubuntu. 

By the way, it's really not possible for me to watch anything on youtube full window. It's really really slow. 

Please let me know if anyone knows the answer, as I really love to use ubuntu, but this problem is really bothering me.

Thanks.

Can you list the specs of the laptop. Sounds to me like you don't have enough RAM.

---

### Post by group256 on 2009-03-30
Thanks for replies.

I thought of graphic card in the first place. if I run the command glxgears it works properly. If any other test comes to your mind let me know, I could get the result of it and put it here. Anyway my specs:

CPU: Celeron 2.4 GHZ
Graphic: Ati IGP 345M(I went round and round to find the suitable driver, no change eventually)
RAM: 512 MB DDRI

Regarding the VGA, the default driver is working right now. I didn't touch it as I couldn't find a more suitable one. In my hardware information it says that it's the driver for ATI IGP 330/340/350M.

I don't think it's RAM problem as I check my used ram constantly and I see that most of the time not more than 300 MB is used.

By the way my laptop model is:

Sony [Vaio PCG-FRV31]("http://www.amazon.com/Sony-PCG-FRV31-Laptop-2-40-GHz-Celeron/dp/B0000E6GHM")

---

### Post by DeMus on 2009-03-30
> **group256 said:**
> Thanks for replies.

I thought of graphic card in the first place. if I run the command glxgears it works properly. If any other test comes to your mind let me know, I could get the result of it and put it here. Anyway my specs:

CPU: Celeron 2.4 GHZ
Graphic: Ati IPG 345M(I went round and round to find the suitable driver, no change eventually)
RAM: 512 MB DDRI

Regarding the VGA, the default driver is working right now. I didn't touch it as I couldn't find a more suitable one. In my hardware information it says that it's the driver for ATI IGP 330/340/350M.

I don't think it's RAM problem as I check my used ram constantly and I see that most of the time not more than 300 MB is used.

By the way my laptop model is:

Sony [Vaio PCG-FRV31]("http://www.amazon.com/Sony-PCG-FRV31-Laptop-2-40-GHz-Celeron/dp/B0000E6GHM")

Do all those things you mentioned, which are so slow in Ubuntu, working on normal speed in XP? If so, we can rule out (lack of) hardware capabilities. What is left is a driver problem probably, the VGA card most likely.

---

### Post by group256 on 2009-03-30
Yeap, all are really normal and smooth. As you mentioned DeMus, Most probably there is something wrong with Graphic Driver, and I did search more than couple of days for its driver and it seems none suitable for this specific card is existed. Somehow, I guess I have to get back to XP again.

---

