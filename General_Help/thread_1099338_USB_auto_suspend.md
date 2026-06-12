---
title: "USB auto suspend"
date: 2009-03-18
forum: General Help
---

### Post by Mr.Carramba on 2009-03-18
hi,

I wondering if ubuntu somehow auto suspends USB which is not used?
I use USB for programing sensors through USB hub. Then testing USB may not be used for some time, then I try to reprogram sensor I too often get "Clock validation error" which makes me wonder is on my laptop USB goes to sleep or gets auto suspended? 

Therefore I wonder if there is a way to dissaible/enable this future.

---

### Post by 3rdalbum on 2009-03-18
You're right: Ubuntu doesn't auto suspend USB by default. At least, that's what I believe.

On my netbook, I installed Intel's Powertop software (sudo apt-get install powertop) that can track down programs and configuration problems that are causing your computer to use more power than necessary. When you run it (run it as root - sudo powertop), it will detect one or two problems and give you the chance to press a particular key to fix those problems. One of them will be the USB auto suspend.

You'd need to run Powertop and apply the fixes each time after you boot up. There should be a way of starting auto suspend each time on bootup, but I have not managed to find out what it is.

---

### Post by Mr.Carramba on 2009-03-18
> **3rdalbum said:**
> You're right: Ubuntu doesn't auto suspend USB by default. At least, that's what I believe.

On my netbook, I installed Intel's Powertop software (sudo apt-get install powertop) that can track down programs and configuration problems that are causing your computer to use more power than necessary. When you run it (run it as root - sudo powertop), it will detect one or two problems and give you the chance to press a particular key to fix those problems. One of them will be the USB auto suspend.

You'd need to run Powertop and apply the fixes each time after you boot up. There should be a way of starting auto suspend each time on bootup, but I have not managed to find out what it is.

oh, this explain things, but now the question is then auto suspend usb is enabled, how to disable it? and where do I check if its enabled or not?

---

