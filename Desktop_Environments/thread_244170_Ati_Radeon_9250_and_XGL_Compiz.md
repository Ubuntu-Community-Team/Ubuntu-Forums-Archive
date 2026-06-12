---
title: "Ati Radeon 9250 and XGL Compiz"
date: 2006-08-26
forum: Desktop Environments
---

### Post by masterspy7 on 2006-08-26
Hi, heres the problem. I have a Sapphire ATI Radeon 9250 PCI 128 MB video card. It works fine with everything, but, recently I tried to installed XGL/Compiz on my Ubuntu system using this guide.

[http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/](http://justpretending.net/wp/2006/08/14/new-and-improved-enable-xglcompiz-on-ubuntu-dapper-drake/)

It did not work, when I tried to log into a XGL Session it gives me the ten second crash. I can post the error details if needed, but first I would like to know if my video card can even handle xgl/compiz and if it doesn't, I wouldn't mind if you said I'm screwed. All I wan't to know is can it work, and if it can, what should I do. I followed the guide exactly how it states. Do I need any sort of open source drivers for my card?

NOTE: I have tested out the Kororaa Live CD, but it also wont boot due to problems with the Xorg configuration, just a note, though it might be helpful.

Any help would be greatly appreciated!:)

---

### Post by Greycloak on 2006-08-26
I have had no luck with my ATI 9200 PCI.  I started a thread about this a few days ago and nobody seems to have an answer. From what I can tell the card should be able to handle it. After all, there are people with Radeon 8500s that are using Xgl/compiz.

Somebody please help us!  I want my eye-candy!

---

### Post by Meck1982 on 2006-08-31
Why don't you guys try AIGLX? This works with the ATI oss driver and has the advantage that you can still run your favourite openGL apps like Tremulous. On my Radeon Mobilty 9000 it works like a charm under KDE. The only thing I have to cope with is reducing the colors to 16bpp. But with your amount of vram perhaps you could go with 24bpp. Just search this forum for "aiglx/compiz". I personally wouldn't spend my time getting XGL to work if you can hav aiglx... Just my suggestion.

---

### Post by empthollow on 2007-10-25
Where did you find an aiglx driver for a 9250?

---

### Post by Sachankara on 2007-10-30
> **empthollow said:**
> Where did you find an aiglx driver for a 9250?

Just use the "radeon" driver in Xorg.

---

