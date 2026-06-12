---
title: "Beowulf Cluster Advice?"
date: 2008-07-24
forum: Education &amp; Science
---

### Post by cinohpa on 2008-07-24
I'm looking to set up a beowulf cluster on some of my home machines. I've been trying to do research on it, but for the most part I haven't found anything recent. All the articles I'm finding are 2-3 years old, I imagine there have to be some more recent cluster solutions?

Thanks.

---

### Post by btmiller on 2008-07-26
Have you looked at [www.clustermonkey.net](www.clustermonkey.net) -- they have some up to date articles. However, there's no "one size fits all" recipe for building a Beowulf (how you set it up often depends on the type of application you want to run), so you're best doing a bit of experimenting. Remember that to use a Beowulf, you need code that is designed to run in parallel accross many machines.

---

### Post by machoo02 on 2008-07-26
Have you read about the [Microwulf project]("http://www.calvin.edu/~adams/research/microwulf/") from Calvin College?  This was a few years back, but they used Ubuntu to build a small, portable Beowulf cluster.  They even have system configuration notes on how they set it up.

---

### Post by KatBuntu on 2008-07-29
There's a project called rockscluster, it has a lot of features and it has a lot of support. 
It's not difficult to build a beowulf with this plataform, you only need some computers and a ethernet switch to connect them, the metod to create and install the nodes and other peripherals is very simple.
This distribution is used in a lot of universities of US and Europe.
In the actual version developers introduced a virtualization feature.

I hope this works for you

[www.rocksclusters.org]("http://www.rocksclusters.org")

---

