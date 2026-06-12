---
title: "Maxima"
date: 2010-03-09
forum: Education &amp; Science
---

### Post by pathematica on 2010-03-09
I note that Maxima (and wxMaxima) is broken in Karmic and it has been broken for some time (and, quite possibly, it might never have worked). The problem is easily demonstrated by attempting to evaluate a variety of basic functions (eg square root). 

I have tried to check whether any useful progress has been made to find a fix. I find the technical sites quite confusing. I note that, of the few sites I have found, a number suggest that Maxima should work in 10.04. 

Whilst I guess that is not too far away now can anybody tell me whether this problem has been abandoned as insoluble for 9.10? It is not clear to me from reading the bug sites whether anyone is still working an attempt to fix it. 

At present, when I need Maxima, I boot into SuSE. 

Anyone with any interest and/or any news?

Thanks

---

### Post by pathematica on 2010-03-10
I think I understand the discussions in the Maxima forums. My impression is that they consider the problem lies with Ubuntu (Karmic) rather than with Maxima so that but reports are marked as "invalid" and closed with a "won't fix" tag.

I am not sure where to look for the equivalent forums in Ubuntu. I cannot work out whether anyone is concerned about this problem. Does Ubuntu aspire to being a complete operating system that will run programs such as Maxima, or are these considered specialist tools that are not sufficiently mainstream to justify bug fixes? No sarcasm is intended, this is a genuine question about the philosophy underlying Ubuntu. If there is an arena within Ubuntu in which the problem with Maxima is being discussed, does anyone know where it is? It's very confusing.

---

### Post by hsweet on 2010-03-11
I can't help, but it would be a shame to lose Maxima.

---

### Post by csaratchand on 2010-03-14
1. Istvan Blahota has created a PPA for Maxima (based on SBCL) and WxMaxima. Get it at: [https://launchpad.net/~blahota/+archive/wxmaxima]("https://launchpad.net/~blahota/+archive/wxmaxima"). Installation proceeds by adding the repository.
2. Camm Maguire has created Maxima (GCL based) and WxMaxima. Get it at: [http://packages.debian.org/sid/math/maxima](http://packages.debian.org/sid/math/maxima). Installation proceeds by manually downloading all maxima packages and their dependencies to a folder such as /home/Desktop/abc.
Next, open a terminal and type ```
cd /home/Desktop/abc
```
Then ```
sudo dpkg -i *.deb
```
In case any dependencies are still unmet, open the Synaptic Package Manager and click on Edit >> Fix Broken Packages.

---

### Post by pathematica on 2010-03-14
Thank you. This has worked exactly as suggested. In fact I do use WxMaxima rather than maxima but the problem applied to both.

---

### Post by beastrace91 on 2010-03-15
> **pathematica said:**
> Thank you. This has worked exactly as suggested. In fact I do use WxMaxima rather than maxima but the problem applied to both.

I posted a thread about this some time ago... There are more than a few packages in the Universe repos that are like this - useless. Honestly it looks bad for Ubuntu, anyone who has been using Ubuntu/Linux before knows how to go download an outside package/add a PPA but it still looks bad for the OS none the less.

~Jeff

---

