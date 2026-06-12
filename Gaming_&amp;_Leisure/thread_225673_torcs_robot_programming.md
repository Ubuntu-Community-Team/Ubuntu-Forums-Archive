---
title: "torcs robot programming"
date: 2006-07-30
forum: Gaming &amp; Leisure
---

### Post by tehquickness on 2006-07-30
Has anyone ever done any robot creation for torcs?? I have looking into their tutorial on it but I am at a complete loss for words. I was wondering if anyone else has already done it before. The info I got from the tutorial says I need these enviormental variables:

export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/lib
export TORCS_BASE=/usr/src/torcs/torcs-1.2.4
export MAKE_DEFAULT=$TORCS_BASE/Make-default.mk

I am not sure where those would be located from the apt-get install of torcs. If I could get some help figuring this out I would be glad to post it as a how-to, tutorial, or guide at the appropriate places(like Ubuntu document storage or the forums)
Thanks in advance.

---

### Post by handy on 2006-07-30
Hopefuly the links at the bottom of [this page]("http://torcs.sourceforge.net/sections.php?op=viewarticle&artid=30"), if the page itself doesn't answer your problem.

---

### Post by Harleen on 2006-07-30
I did program a robot for TORCS. But it wasn't as much fun as I expected and my robot wasn't nearly competitive, so I dropped it.
The easiest way to develop a robot for TORCS is to compile TORCS from source. That way you have all sources at one place and can follow the tutorial without any change.
If you use the Ubuntu version, you have to check out the source for that version, too. I haven't done this before, as I used the source code from that site. It should be possible with "sudo apt-get source torcs", but I'd suggest to remove the Ubuntu packages and start with the source package folowing these instructions: [http://torcs.sourceforge.net/sections.php?op=viewarticle&artid=3#linux-src-all](http://torcs.sourceforge.net/sections.php?op=viewarticle&artid=3#linux-src-all)

Hmm, maybe I should pick up that robot again...

---

### Post by tehquickness on 2006-07-30
ok, well i will just build it from src then that will be the easiest. maybe we can get Team Ubuntu going for torcs

---

