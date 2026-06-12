---
title: "Debian as a server with no hardware firewall"
date: 2008-06-19
forum: Debian
---

### Post by asmith3006 on 2008-06-19
Hi, I'm really getting into using Ubuntu at home and loving it. My boss has heard about this and now I'm the company linux guy.

So, we're installing three linux servers in our rack hosted in a data centre which will obviously be directly connected to the net. The data center are suggesting we have a Cisco firewall for them. The servers are going to be used for video streaming to several thousand people so will have a large throughput (>1.5GBps) and will be running Debian as that's what the Data Center insist on.

My question is, do we need the firewall? It will be simply for security if we had it. I was lead to believe that linux was very secure and so an extra firewall is pointless.

The reason I'm asking is because the cisco router costs >£10,000 which is obviously an expense we'd like to avoid.

Thanks for any and all advice.

---

### Post by kerry_s on 2008-06-19
a hardware firewall is always a good idea, i'm surprised you didn't have 1 already.
if cost is a factor i suggest just doing your own.
you could recycle a computer or get 1 to use as a firewall.look here->
[http://distrowatch.com/search.php?category=Firewall&origin=All&basedon=All&desktop=All&architecture=All&status=Active](http://distrowatch.com/search.php?category=Firewall&origin=All&basedon=All&desktop=All&architecture=All&status=Active)

---

### Post by asmith3006 on 2008-06-19
We do have one currently, but it's only for a web server or two so the maximum throughput of that is about 100Mbps apparently. These high end CISCO routers are a bit beyond me.

As I said, this is for a high bandwidth project so needs a chunky router and Cisco seem to charge you through the nose for that.

So would something like m0n0wall be a good alternative then? I don't think the boss would be happy with the idea of recycling an old system but he would be happy with spending ~£1000 on a decent box to run it as a router would cost >£10,000

---

### Post by kerry_s on 2008-06-19
honestly, i'd spend the money and get the cisco, it will be more specialized to your needs and probably a lot easier to work with.

---

### Post by asmith3006 on 2008-06-20
Humm. I was hoping you wouldn't say that! Ah well. Thanks for the advice, that's probably what we will do.

---

