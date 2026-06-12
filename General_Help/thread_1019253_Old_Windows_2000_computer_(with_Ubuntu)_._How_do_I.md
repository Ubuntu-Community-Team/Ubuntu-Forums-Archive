---
title: "Old Windows 2000 computer (with Ubuntu) . How do I connect to wireless internet?"
date: 2008-12-22
forum: General Help
---

### Post by Joe5450 on 2008-12-22
Is there anyway? Or must I take a telephone cable from the back into the modem... I really do not want to do this as the modem is far away.

---

### Post by Nathan Sweeney on 2008-12-22
What type of wireless card do you have?

```
lspci -v
```

That should let you know what card you have so that you can get it set up under ubuntu.

---

### Post by Joe5450 on 2008-12-22
I'm currently doing this on my laptop. When I used to log onto it through the windows 2000 it demanded dailup connection.

I don't think it has a wireless card :/

Do I need one? How much are they? o.o how do I install them Q.Q

---

### Post by abn91c on 2008-12-22
> **Joe5450 said:**
> I'm currently doing this on my laptop. When I used to log onto it through the windows 2000 it demanded dailup connection.

I don't think it has a wireless card :/

Do I need one? How much are they? o.o how do I install them Q.Q
if it has a PCIMCA Slot on the side you can get one at walmart, a wireless G card is about $45-60 depending on brand.  Installation will depend on the chip set of the card you get, if you are lucky ubuntu will find it automatically, if not there are many guides in the forums for wireless cards.

---

### Post by Joe5450 on 2008-12-22
And if there is no slot then... I must connect to modem directly?

---

### Post by abn91c on 2008-12-22
the slot is about the size of a credit card, usually one the side of the laptop, if it has usb port a belkin USB adapter works with ubuntu.
By the way what brand/specs is the laptop

---

### Post by Nathan Sweeney on 2008-12-22
Are you still using dial up or do you have cable or DSL internet now?

You will need to have a wireless card in your computer as well as a wireless router to be your access point.

What is the model you are trying to use?  There are wireless cards that would fit into say pcmia slots and also wireless adapters that you can just connect to usb.  You would need to research which ones work best with linux, as I don't use them.  Price wise I would say that you are looking at around $50 or in that range.

---

### Post by Joe5450 on 2008-12-23
I currently have wireless DSL. The computer I put ubuntu on, I found on the side of the road. 

It worked just fine with windows 200 but demanded a dailup connection. It has USB slots so if there are wireless adapters for usb I'll have to look into that. Thank you.

---

### Post by TeXtonyx on 2008-12-23
This may not be so easy because a computer that old probably
uses USB 1.1 I think it is, not USB 2, so you would need to 
find a backward compatible card. I think you better take it 
with you to one of those big computer stores. Maybe the bios
can be upgraded.

---

