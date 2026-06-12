---
title: "Inspiron 1420N performance: upgrade CPU or RAM? or save $50?"
date: 2008-03-26
forum: Dell  Ubuntu Support
---

### Post by tlroche on 2008-03-26
I've been running linux servers for a while, but only win32 clients, though on my own laptops I've run pretty much exclusively OSS (e.g. Cygwin for bash and other GNU tools, Firefox, Thunderbird, GIMP). I'd like to ease into a linux client, so I'm considering getting one of the Dell Inspiron 1420N with Ubuntu preloaded.

I'm dithering over build options. I notice the default processor="Pentium Dual Core T2330 (1.6GHz/533Mhz FSB/1MB cache)" and the default RAM="1GB Shared Dual Channel DDR2 at 667MHz". However the main "Dell PCs Featuring Ubuntu" page says default processor="Intel Core 2 Duo T5450 (1.66GHz/667Mhz FSB/2MB cache)": I asked Dell Chat about that yesterday, and they just said, "the main page is wrong, the default is the Pentium."

What I really want is a smaller faster HD for the same price as the default (default=120GB 5400rpm, preference=80GB 7200rpm) but that's not an option--instead I'd hafta pay $150 for a 160GB 7200rpm :-( However for $50 I can either

* upgrade the processor to "Intel Core 2 Duo T5450 (1.66GHz/667Mhz FSB/2MB cache)"

* double the memory to "2GB Shared Dual Channel DDR2 at 667MHz"

I'm wondering if it's worth upgrading the processor to make its FSB speed match the RAM speed, plus get more cache (and, IIRC, save power). OTOH if this was gonna be a win32 system, I'd definitely get more memory.

Would I get a better performance improvement with the processor upgrade or the RAM upgrade, or will the performance improvement likely be negligible either way and I'd be better off saving the $50? And will ordering any modification to the base configuration cause my delivery to be delayed by weeks ?-)

TIA, Tom_Roche at pobox.com

---

### Post by Trindol on 2008-03-26
I'd go with the RAM I guess, 1 GB is becoming the minimum. Might as well stay ahead a little even if it's not totally necessary. I doubt it will affect shipping. I changed a bunch of things in my order from Dell recently and it shipped very quickly, faster than they "estimated"

Is it any cheaper to buy it without Windows and just Ubuntu? Mine wasn't, just wondering if they have changed this. And what version of Ubuntu are they shipping with now?

---

### Post by fragos on 2008-03-26
The biggest performance increase of more memory relates to swapping.  At 1GB and desktop applications I basically never use any swap space on the disk.  The System Monitor or free on the command line will tell you if you're using swap.  I have a 1420n and a desktop with an AMD Sempron 2800+.  Both have 1GB but the desktop does have a 7200 RPM IDE with 8MB cache.  Although subjective, the desktop seems faster when loading applications.  Drive speed would be the next place I look to gain improvement in the 1420n.  Just my thoughts.

---

### Post by tlroche on 2008-03-26
> **Trindol said:**
> I changed a bunch of things in my order from Dell recently and it shipped very quickly, faster than they "estimated"

That's good to hear.

> **Trindol said:**
> Is it any cheaper to buy it without Windows and just Ubuntu? Mine wasn't, just wondering if they have changed this.

Apparently yes: the current "Dell PCs Featuring Ubuntu" page

[http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs](http://www.dell.com/content/topics/segtopic.aspx/linux_3x?c=us&cs=19&l=en&s=dhs)

shows a base configuration "Inspiron Laptop 1420 N" for $599, while the main "Dell Inspiron 1420 Laptop Product Details" page

[http://www.dell.com/content/products/productdetails.aspx/inspnnb_1420?c=us&cs=19&l=en&s=dhs&~ck=mn](http://www.dell.com/content/products/productdetails.aspx/inspnnb_1420?c=us&cs=19&l=en&s=dhs&~ck=mn)

shows apparently the same configuration for $649. (Note that both have processor="Pentium Dual Core T2330 (1.6GHz/533Mhz FSB/1MB cache)")

> **Trindol said:**
> And what version of Ubuntu are they shipping with now?

"Ubuntu Linux version 7.10 with DVD Playback"

---

### Post by tlroche on 2008-03-26
> **tlroche said:**
> What I really want is a smaller faster HD for the same price as the default (default=120GB 5400rpm, preference=80GB 7200rpm) but that's not an option--instead I'd hafta pay $150 for a 160GB 7200rpm :-( However for $50 I can either

* upgrade the processor to "Intel Core 2 Duo T5450 (1.66GHz/667Mhz FSB/2MB cache)"

* double the memory to "2GB Shared Dual Channel DDR2 at 667MHz"

...

Would I get a better performance improvement with the processor upgrade or the RAM upgrade, or will the performance improvement likely be negligible either way and I'd be better off saving the $50?

> **fragos said:**
> Drive speed would be the next place I look to gain improvement in the 1420n.

I'd definitely prefer a faster drive if Dell didn't make that option so bleeping expensive.

Just to clarify: are you saying that you'd add more memory first, and then improve drive speed? or the other way around?

TIA, Tom_Roche at pobox.com

---

