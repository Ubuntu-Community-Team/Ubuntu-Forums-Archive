---
title: "drag-and-drop with dell inspiron 10 mini touchpad"
date: 2009-11-11
forum: Dell Ubuntu Support (CLOSED)
---

### Post by fresh08 on 2009-11-11
Hi, does anybody else have problems when they try to drag-and-drop with their touchpad on the inspiron mini 10 under ubuntu? The touchpad works fine when I just use one finger, but one I also click and hold to do drag and drop of files or to select text, the mouse pointer flies to the top left corner. I've changed the mouse sensitivity settings, etc, but I can't get it to work. It's really frustrating.

I am also raising this with Dell, but it's kind of silent on their side... My laptop came shipped with ubuntu 8 and I've installed 9.04 myself. Personally I think the touchpad is broken, but I want to make sure it's not ubuntu 9.04 (which is mostly like the first question/claim of the Dell Support).

Does anybody else experience this and is there a way to resolve it?

Davy

System: Inspiron mini 10 with Ubuntu version 9 netbook installed

---

### Post by mikewhatever on 2009-11-11
Here is how I drag and drop, tap twice on the file you want to drag, leaving the finger on the touchpad after the second tap, then drag. This way, you never need to left click or the other hand.

---

### Post by Devi 710 on 2009-11-11
There are a lot of posts about this. You can try this (it is for karmic):

[http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook]("http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook")

---

### Post by mikewhatever on 2009-11-11
I've had no chance to verify it, but others said one of the models had a Gsynaptics touchpad, while the other an Elantec one (the two models are mini 10 and mini 10v). 'sudo lshw' doesn't mention either vendor, so I really don't know if that's true.

---

### Post by Devi 710 on 2009-11-11
That is a good point. 
I have a 10v and it may be different. Perhaps looking for a solution specific to the Mini 10 would be better.

---

### Post by fresh08 on 2009-11-19
> **Devi 710 said:**
> There are a lot of posts about this. You can try this (it is for karmic):

[http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook](http://linuxcentre.net/wiki/index.php/Ubuntu_Karmic_Koala_on_the_Dell_Mini_10v_Netbook)

thanks, I've upgraded my system to Karmic and tweaked the mouse sensitivity settings a bit and it works! Thanks for the tips.

As a second plan, it was also useful to know that you can do drag-and-drop with tapping the touchpad and holding after the second tap and than drag.

---

