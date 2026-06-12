---
title: "ATi with AIGLX..."
date: 2007-06-10
forum: Desktop Effects &amp; Customization
---

### Post by FA22RaptorF22 on 2007-06-10
I have just realized a disturbing discovery.  We all know how ATI does not have a driver that yet supports AIGLX.  In booting a live cd on Ubuntu Fiesty, i found myself using beryl instantly.  This happened on an older laptop with an ATi Radeon 7500.  This is an older card.  It seems that older cards are capable of integrating with AIGLX with the proprietary driver.  The result is very nice i might add, and will still hope one day that ATI comes up with a driver for the newer cards.  Anyone else experience this?  I think its really cool and sad at the same time. :popcorn:

---

### Post by kenbo on 2007-06-10
I had success using AIGLX with the radeon driver with my X800XT It&#347; not the fastest it could be but it works well enough.

---

### Post by 444 on 2007-06-11
I have a 7500. It's actually not supported by ATI. There is a very good open source driver for it. Downside is I don't get PowerPlay :( ...

---

### Post by Kubunteando on 2007-06-11
Don't get confused there.
The Ubuntu Feisty uses the ATI Open Source drivers with Direct Rendering by default which works really nicely in older cards like radeon r200, r200 and r280. For newer cards you need to check the compatibility in:

[http://dri.freedesktop.org/wiki/Status](http://dri.freedesktop.org/wiki/Status)

With those and Feisty which uses X.Org 7.2 Beryl seems a way much more stable.

---

### Post by kpolice on 2007-06-11
It's more stable but still slower than the propietary driver and you lose powerplay and other features. I still prefer the propietary driver + xgl if I want Compiz.

And my notebook runs cooler with the fglrx driver.

---

