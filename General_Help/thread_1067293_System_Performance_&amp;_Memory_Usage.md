---
title: "System Performance &amp; Memory Usage"
date: 2009-02-11
forum: General Help
---

### Post by Heliophion on 2009-02-11
Out of curiosity, would Ubuntu 8.10 be expected to run faster on a 2GB Intel Celeron system with 2GB RAM or a 2GB Pentium 4 with 1GB RAM?

Also, in system monitor, my memory usage runs at about 20% (400MB of 2GB) when running no apps. Is that normal? It seems a bit high to me. And if that is normal, how do systems with 256MB - 512MB handle Ubuntu 8.10? Does performance decrease significantly with that amount of memory? Are they using more swap?

---

### Post by jenkinbr on 2009-02-13
Your Proccessor specs are confusing me a bit.

About your ram usage, a lot of that is probably just cache, and is probably normal. I have a 512MB machine at home that runs fine with most of the RAM taken up from the beginning.  It simply swaps out junk that isn't used.

---

### Post by jerome1232 on 2009-02-13
Did you mean to say a 2Ghz Celeron /w 2 GB of RAM vs a 2Ghz Pentium 4 /w 1 GB of RAM?

It really depends on how you use your system, some applications are cpu intensive some are memory hogs, if you do alot of ram hogging then more ram will be good for you, if you do cpu intensive tasks then the Pentium 4 will be better, since the pentium 4 should have better cache sizes and etc than the Celeron will.

---

### Post by fragos on 2009-02-14
For me there's little benefit of installing past 1GB of memory. Run "free" and it will tell you if you're using any swap space. At 1GB I almost never use swap space. Swap space use is important since swap is from/to disk. Memory is a relatively inexpensive hardware upgrade. Foe memory two is better than one. It's my understanding for example that 2 512MB simms of the same specs will have 10% faster performance than one 1GB simm.

---

### Post by Slim Odds on 2009-02-14
> **fragos said:**
> It's my understanding for example that 2 512MB simms of the same specs will have 10% faster performance than one 1GB simm.

What makes you think this?

---

### Post by fragos on 2009-02-14
> **Slim Odds said:**
> What makes you think this?

I can't point to a specific source but have read this in a number of places. I believe it has to do with the ability to double the wide of memory access when two equal simms are installed. I'd think that's why memory slots come in pairs. DDR stands for Double Data Rate. [http://en.wikipedia.org/wiki/DDR_SDRAM](http://en.wikipedia.org/wiki/DDR_SDRAM)

---

### Post by jespdj on 2009-02-14
When you have two memory modules instead of one, then the system can use them both at the same time (because the chipsets for most Intel processors from the Pentium to the Core 2 Duo have a **dual channel** memory interface). When you have just one memory module, then dual channel doesn't work and accessing the RAM might be a bit slower.

The new Intel Core i7 processors even have a triple channel memory interface, which means it's best to use triplets of memory modules.

---

### Post by Slim Odds on 2009-02-14
> **jespdj said:**
> When you have two memory modules instead of one, then the system can use them both at the same time (because the chipsets for most Intel processors from the Pentium to the Core 2 Duo have a **dual channel** memory interface). When you have just one memory module, then dual channel doesn't work and accessing the RAM might be a bit slower.

The new Intel Core i7 processors even have a triple channel memory interface, which means it's best to use triplets of memory modules.

This **only** applies to motherboards that are **dual channel**. It's not a universal thing and most older boards would not have this.

If you have a dual channel board, then by all means populate in pairs.

---

### Post by Slim Odds on 2009-02-14
> **fragos said:**
> I can't point to a specific source but have read this in a number of places. I believe it has to do with the ability to double the wide of memory access when two equal simms are installed. I'd think that's why memory slots come in pairs. DDR stands for Double Data Rate. [http://en.wikipedia.org/wiki/DDR_SDRAM](http://en.wikipedia.org/wiki/DDR_SDRAM)

DDR and dual channel are two completely different things.

Dual channel boards might have pairs of slots, but other older boards that don't have dual channel don't need to.

My motherboard is a few years old and uses DDR. I has 3 memory slots (it's not dual channel).

BTW, if you read that article you'll see what DDR really means: > It achieves nearly twice the [bandwidth]("http://en.wikipedia.org/wiki/Bandwidth_%28computing%29") of the preceding "single data rate" [SDRAM]("http://en.wikipedia.org/wiki/SDRAM") by [double pumping]("http://en.wikipedia.org/wiki/Double_data_rate") (transferring data on the rising and falling edges of the [clock signal]("http://en.wikipedia.org/wiki/Clock_signal")) without increasing the clock frequency.

[http://en.wikipedia.org/wiki/Dual-channel_architecture](http://en.wikipedia.org/wiki/Dual-channel_architecture)

---

### Post by Heliophion on 2009-02-16
> **jerome1232 said:**
> Did you mean to say a 2Ghz Celeron /w 2 GB of RAM vs a 2Ghz Pentium 4 /w 1 GB of RAM?

Yes, that's what I meant.

---

### Post by handy on 2009-02-17
You might enjoy [*_htop_*]("http://htop.sourceforge.net/"), try typing htop in your terminal, if nothing happens it is not installed, so you might like to install it with synaptic, it gives you a lot of info' & is very light itself.

---

### Post by jenkinbr on 2009-02-17
> **handy said:**
> You might enjoy [*_htop_*]("http://htop.sourceforge.net/"), try typing htop in your terminal, if nothing happens it is not installed, so you might like to install it with synaptic, it gives you a lot of info' & is very light itself.
+1

htop is awesome!

---

