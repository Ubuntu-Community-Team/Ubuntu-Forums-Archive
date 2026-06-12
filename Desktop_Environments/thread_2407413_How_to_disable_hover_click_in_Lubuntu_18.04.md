---
title: "How to disable hover click in Lubuntu 18.04?"
date: 2018-12-03
forum: Desktop Environments
---

### Post by explodyboompow on 2018-12-03
Exactly what it says on the tin. I've got Lubuntu 18.04 installed and I can't seem to find any sort of setting to disable hover click, and endless googling/forum combing hasn't done me much good. Am I as blind and stupid as I feel, or is there some sort of trick to disabling hover click?

The keyboard and mouse config menu doesn't give me the option, and I haven't had much luck trying to fix the issue with something like mousetweaks.

---

### Post by Rex Bouwense on 2018-12-04
Are you talking about raising the window when the cursor hovers over it?  That can be disabled in Openbox Configuration under mouse.

---

### Post by explodyboompow on 2018-12-05
No, I'm speaking of the autoclick. If I rest the cursor for 1 second (I think it's 1 second) then it will automatically click on whatever it's hovering over. This frequently happens when I'm typing - I'll be at the bottom of a paragraph, and my mouse will click into the middle causing me to insert random passages where they don't belong.

I can't reliably reproduce this by just moving and resting my cursor either, and after a few more hours of investigation. I'm beginning to think it might be a hardware issue.

---

### Post by CatKiller on 2018-12-06
It doesn't automatically click.

I suspect that you are using a laptop.

---

### Post by Rex Bouwense on 2018-12-06
Aah CatKiller (nice nick) you are probably correct because that occasionally happens to me when I am using one of my laptops.  explodyboompow, you can either place the cursor off the document that you are working on or disable your touchpad while you are working on it.  What is more than likely happening is your hand is brushing up against your touch pad and causing it to move the cursor on your screen.

---

### Post by bradhaack on 2018-12-08
I have recently installed lubuntu on an old macbook  It sure seems like hover click is engaged, but after experimenting I think the track pad may be set up too sensitive.  I'm getting way more inadvertent clicks than I did when it was running osx.    Similar behavior to the OP.    Is there a setting for sensitivity?

---

### Post by CatKiller on 2018-12-08
> **bradhaack said:**
> Is there a setting for sensitivity?
The term you're looking for is *palm rejection*. My understanding is that it's sometimes a bit spotty, and some trackpads are better supported than others, but mine has always been fine so it's not something I've looked into in any depth.

---

### Post by bradhaack on 2018-12-08
I'm trying PalmDetect=1, FingerHigh=80.   I haven't tested it much yet since I'm using a mouse right now, and turning off the trackpad with  
> synclient touchpadoff=1

---

