---
title: "Installed Savage 2...now what?"
date: 2009-01-15
forum: Gaming &amp; Leisure
---

### Post by wolfyking2 on 2009-01-15
yes, I installed it.  Now what?  I went in the folder but there was no launch or anything, and there's no icon on desktop.

---

### Post by wolfyking2 on 2009-01-15
Ok, I found out were to play it, but when I click on it, it just flashes black.  Help?

---

### Post by Grishka on 2009-01-15
> **wolfyking2 said:**
> Ok, I found out were to play it, but when I click on it, it just flashes black.  Help?

run it from the terminal and post errors here.

---

### Post by wolfyking2 on 2009-01-15
Got the error: Segmentation fault

---

### Post by Perfect Storm on 2009-01-15
Video card?

---

### Post by wolfyking2 on 2009-01-15
I have no idea :<

---

### Post by Perfect Storm on 2009-01-15
> **wolfyking2 said:**
> I have no idea :<

```
lspci | grep VGA
```

---

### Post by wolfyking2 on 2009-01-15
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
I didn't know what it mean't so I just posted it

---

### Post by Perfect Storm on 2009-01-15
Your card doesn't support OpenGL 2.0, so you can't play savage2

Intel cards only support up to v.1.5 for now.

Is it a laptop you have?

---

### Post by wolfyking2 on 2009-01-15
Wow...that sucks...can it play savage 1? >.>

---

### Post by Perfect Storm on 2009-01-15
I don't know, give it a try.

---

### Post by wolfyking2 on 2009-01-15
oh, and I don't have a laptop, this is a dell computer

---

### Post by wolfyking2 on 2009-01-15
oh!  would savage 2 work on wine?

---

### Post by Perfect Storm on 2009-01-15
> **wolfyking2 said:**
> oh!  would savage 2 work on wine?

I have no idea. I only run native linux games. But I guess it requires some horse power card to work either way and intel cards is long way from muscle card.

But if you can get your hand on a nvidia card you should go for that.

EDIT:

Minimum:
Processor - 2.2GHz Pentium 4 / AMD 2000+ or faster
RAM - 1GB of RAM
Video Card - 128MB fully OpenGL 2.0 / GLSL 1.20 compliant Geforce or Radeon
Network Connection Required 

Recommended:
Processor - 2.0GHz Core 2 Duo / AMD 3500+ or faster
RAM - 1.5GB or higher
Video Card - 256MB Geforce 7800+ or Radeon X1900+
Network Connection Required (Broadband)

---

### Post by wolfyking2 on 2009-01-15
Don't see why we could just spend 300 more friggin dollars too buy a NEW computer...parents had to buy a 5 year old USED computer...>.>:mad:

---

### Post by eragon100 on 2009-01-15
> **Artificial Intelligence said:**
> I have no idea. I only run native linux games. But I guess it requires some horse power card to work either way and intel cards is long way from muscle card.

But if you can get your hand on a nvidia card you should go for that.

EDIT:

Minimum:
Processor - 2.2GHz Pentium 4 / AMD 2000+ or faster
RAM - 1GB of RAM
Video Card - 128MB fully OpenGL 2.0 / GLSL 1.20 compliant Geforce or Radeon
Network Connection Required 

Recommended:
Processor - 2.0GHz Core 2 Duo / AMD 3500+ or faster
RAM - 1.5GB or higher
Video Card - 256MB Geforce 7800+ or Radeon X1900+
Network Connection Required (Broadband)

The windows version of savage 2 has a directx renderer, and seems to work (at least for the most part) under wine:

[http://appdb.winehq.org/objectManager.php?sClass=version&iId=10678](http://appdb.winehq.org/objectManager.php?sClass=version&iId=10678)

---

### Post by wolfyking2 on 2009-01-15
Hmm...must be reason why, didn't install Directx XD  it said there was an error, that musta been it.  I'm trying EVE online right now, so I'll try Savage 2 later

---

### Post by wolfyking2 on 2009-01-15
Darn, when I tried to install the Directx, it gave me some error :(

---

### Post by Grishka on 2009-01-15
> **wolfyking2 said:**
> Darn, when I tried to install the Directx, it gave me some error :(

there's no need to install directx under wine. wine automatically translates directx calls to opengl. anyway, you should really change your video card if you're into gaming. many games will not work with it.

---

### Post by merlyn on 2009-01-16
> **wolfyking2 said:**
> Don't see why we could just spend 300 more friggin dollars too buy a NEW computer...parents had to buy a 5 year old USED computer...>.>:mad:

Chances are you have an unoccupied AGP slot.

I'm betting you could pick up a video card for much less than $300.00, and install that.

Cheers.

---

### Post by wolfyking2 on 2009-01-16
Uhh...last time I checked 12 year olds don't have 300$ and don't know how to install video cards ):P

---

### Post by Grishka on 2009-01-16
> **wolfyking2 said:**
> Uhh...last time I checked 12 year olds don't have 300$ and don't know how to install video cards ):P

get a job and learn to install video cards then. or ask your mum, kid. :P

---

### Post by wolfyking2 on 2009-01-16
My mom isn't like that :P

---

### Post by merlyn on 2009-01-18
> **wolfyking2 said:**
> Uhh...last time I checked 12 year olds don't have 300$ and don't know how to install video cards ):P

Fair enough.

However, given that I'm not psychic, and that it is otherwise impossible to determine age, employment status and other such particulars from reading forum posts, it was sound advice.

Cheers.

---

