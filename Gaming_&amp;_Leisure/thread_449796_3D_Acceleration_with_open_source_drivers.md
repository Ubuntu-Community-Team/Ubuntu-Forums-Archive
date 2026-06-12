---
title: "3D Acceleration with open source drivers?"
date: 2007-05-20
forum: Gaming &amp; Leisure
---

### Post by viciouslime on 2007-05-20
Are there any cards/chipsets out there that can use 3d acceleration but through open drivers, i.e. not ATI or Nvidia cards. I know the intel drivers are open source, but all their chips seem to be for onboard only.

---

### Post by The Noble on 2007-05-20
What Manufacturer out there makes cards besides ATI, Intel, and Nvidia? ATI has some older cards that run using the open source radeon driver, but it sounds like you don't want that...

---

### Post by viciouslime on 2007-05-21
> **The Noble said:**
> What Manufacturer out there makes cards besides ATI, Intel, and Nvidia? ATI has some older cards that run using the open source radeon driver, but it sounds like you don't want that...

No, I didn't think there would be any, but I thought it was worth asking.

---

### Post by bastiegast on 2007-05-21
Yup, intel, but you wouldn't want to use that for gaming.

---

### Post by Enverex on 2007-05-21
> **bastiegast said:**
> Yup, intel, but you wouldn't want to use that for gaming.

He already said that...

> **viciouslime said:**
> No, I didn't think there would be any, but I thought it was worth asking.

Matrox, VIA, SiS... although those are very few and far-between these days.

Your only real option is old ATi cards supported by the ati/radeon open source driver (I think any Radeon using the R200 chipset is best supported).

---

### Post by bastiegast on 2007-05-21
> **Enverex said:**
> He already said that...

Bummer! And I always go mad about people who don't read posts.

---

### Post by meldroc on 2007-05-21
AMD, which recently bought ATI, has promised to open-source the ATI drivers, though they haven't done it yet.

There's a project called Nouveau, who's goal is to reverse-engineer Nvidia's hardware programming protocol and create fully 3-D accelerated open-source drivers.  They're not ready for prime time yet, but they seem to be making a lot of progress lately.

Intel's drivers are open source, but Intel onboard GPU chipsets suck.  They don't have T&L, and they share main memory with the rest of the system instead of having their own video memory.  That's good enough for desktop applications, and they have rudimentary 3-D acceleration which is good enough for old games, but new games will choke on these turkeys.

---

### Post by viciouslime on 2007-05-22
> **meldroc said:**
> AMD, which recently bought ATI, has promised to open-source the ATI drivers, though they haven't done it yet.

There's a project called Nouveau, who's goal is to reverse-engineer Nvidia's hardware programming protocol and create fully 3-D accelerated open-source drivers.  They're not ready for prime time yet, but they seem to be making a lot of progress lately.

Intel's drivers are open source, but Intel onboard GPU chipsets suck.  They don't have T&L, and they share main memory with the rest of the system instead of having their own video memory.  That's good enough for desktop applications, and they have rudimentary 3-D acceleration which is good enough for old games, but new games will choke on these turkeys.

I knew about nouveau, but I wasn't aware of AMD saying they would opensource the ATI drivers, that is good news!

---

### Post by lakersforce on 2007-05-22
> **viciouslime said:**
> I knew about nouveau, but I wasn't aware of AMD saying they would opensource the ATI drivers, that is good news!

Yeah, that is good news. If that happens I will instantly discard my Nvidia card :D

---

### Post by viciouslime on 2007-05-22
> **lakersforce said:**
> Yeah, that is good news. If that happens I will instantly discard my Nvidia card :D

Ditto!

---

### Post by Enverex on 2007-05-22
> **lakersforce said:**
> Yeah, that is good news. If that happens I will instantly discard my Nvidia card :D

It's unofficial and most people don't believe it will happen. I live in hope, but that's happened too many times and most people are still living in hope for things that will never happen.

---

### Post by God Of Atheism on 2007-05-22
If AMD  truly wants to release the source code for the ATI drivers, why do they state their intentions instead of just doing so? Since they bought ATI they own the source code and can release it immediately, no need for announcements before doing so.

---

### Post by viciouslime on 2007-05-22
> **Enverex said:**
> It's unofficial and most people don't believe it will happen. I live in hope, but that's happened too many times and most people are still living in hope for things that will never happen.

I don't think it is unofficial, if you search around it was officially announced. Of course, until it happens that doesn't mean much.

---

### Post by viciouslime on 2007-05-22
> **God Of Atheism said:**
> If AMD  truly wants to release the source code for the ATI drivers, why do they state their intentions instead of just doing so? Since they bought ATI they own the source code and can release it immediately, no need for announcements before doing so.

It might not be that simple, if the current code contains third-party licensed code, then they won't be able to do this. Nvidia have said before that the reason they don't open-source their drive is because it currently contains code that they don't own. Though I am sure they could have coded round that by now if they wanted to. In ATI's case however the announcement was only made about a week ago, so I think we should give them some time before judging them. I feel quite positive about this.

---

### Post by meldroc on 2007-05-22
What really bugs me about both Nvidia and ATI is that they not only won't open-source their drivers, but they also refuse to disclose register-level/bus-level programming information about their cards without an NDA.  If that information was available, the X.org people would have written their own drivers long ago.  If you look at the X.org source at the open source nv 2-d only drivers, you'll notice that they've been run through a code obfuscation tool to make it very difficult to use it to figure out how the cards work - the X.org developers were required to do this by their agreement with Nvidia (who helped them write the open-source drivers.)

That's why Nouveau isn't working yet - they have to reverse-engineer the Nvidia cards by peeking at the data going between the card and the rest of the system while running test operations.  They have to be very careful when doing this to ensure they don't accidentally peek under the hood of the driver itself - the driver must be an inviolate black box, or their knowledge is contaminated, and if they write their own driver with that knowledge, Nvidia will sue their asses.

My theory is that Nvidia and ATI refuse to disclose hardware programming specs because some of the registers control things like DRM features.  Any video card with a TV out will have Macrovision built into it.  And it's likely that if you know exactly which register to twiddle, you can turn Macrovision on and off at will, enabling you to violate the DMCA and do things like send un-Macrovisioned video output of DVDs.  Nvidia and ATI have been bought by the MPAA.

---

### Post by viciouslime on 2007-05-22
> **meldroc said:**
> What really bugs me about both Nvidia and ATI is that they not only won't open-source their drivers, but they also refuse to disclose register-level/bus-level programming information about their cards without an NDA.  If that information was available, the X.org people would have written their own drivers long ago.  If you look at the X.org source at the open source nv 2-d only drivers, you'll notice that they've been run through a code obfuscation tool to make it very difficult to use it to figure out how the cards work - the X.org developers were required to do this by their agreement with Nvidia (who helped them write the open-source drivers.)

That's why Nouveau isn't working yet - they have to reverse-engineer the Nvidia cards by peeking at the data going between the card and the rest of the system while running test operations.  They have to be very careful when doing this to ensure they don't accidentally peek under the hood of the driver itself - the driver must be an inviolate black box, or their knowledge is contaminated, and if they write their own driver with that knowledge, Nvidia will sue their asses.

My theory is that Nvidia and ATI refuse to disclose hardware programming specs because some of the registers control things like DRM features.  Any video card with a TV out will have Macrovision built into it.  And it's likely that if you know exactly which register to twiddle, you can turn Macrovision on and off at will, enabling you to violate the DMCA and do things like send un-Macrovisioned video output of DVDs.  Nvidia and ATI have been bought by the MPAA.

That especially sucks for the 90% of the world who don't give a crap about stupid American organisations that sue the pants off everything they can...

---

