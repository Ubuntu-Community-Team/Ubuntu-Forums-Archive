---
title: "Help tuning Ubuntu 5.10"
date: 2006-01-05
forum: General Help
---

### Post by dj50 on 2006-01-05
Hello,

I've installed Ubuntu on an old computer (Cyrix 266Mhz, 192Mb RAM, GeForce2MX400 64mb) and it isn't very responsive. I wasn't expecting peak performance but I was expecting it to be usable with a little patience. The biggest problem I have is that the GUI is not very responsive (you can see the windows being drawn at some times). I've installed it on a 10GB IBM HDD, allowing Ubuntu to partition it (I have 2 partitions - 9gb and 4-500mb swap).

I think the processor is the bottleneck, and I would appreciate some advice on how to ease the load on it or on whatever might keep ubuntu running slow.

Thanks.

---

### Post by bjourne on 2006-01-05
There are some simple things you can do:

1. Turn off anti-aliasing. System->Preferences->Fonts Details->Smoothing select None. This requires you to have fonts which look good without anti-aliasing so I'd recommend you install the mswebfonts package.

2. Turn on reduced resources mode in Metacity. Program->System Tools->Configuration Editor goto /apps/metacity/general/reduced_resources and check the checkbox. Unfortunately, this makes moving windows look ugly as hell. It is also slightly buggy.

3. Use less resource intensive programs. For example, Epiphany is much faster than Firefox but doesn't have all the nice features Firefox have.

4. Use a faster Metacity theme. The default theme, Human, is quite slow but Simple should be a bit faster.

It is a known fact that Breezy is slower than Hoary for various reasons. So for old and slow machines, I'd say it's smarter to stick with Hoary unless you plan to upgrade.

---

