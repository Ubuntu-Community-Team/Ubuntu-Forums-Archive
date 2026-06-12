---
title: "Konqueror / kio_http concurrency settings"
date: 2006-04-27
forum: Desktop Environments
---

### Post by Xianath on 2006-04-27
Hi all,

A few months back I ran into a problem where the web site I was using at work suddenly became dead slow for Konqueror. I update my box daily, and I can't tell whether it was a site update or an Ubuntu update but it's been impossible since. In Firefox it opens a page in 1-2 seconds, in Konqueror it takes over a minute, sometimes 2.

That website uses a lot (500+) of spacer.gif 1-pixel spacers and Konqueror seems to be neither parallelizing nor pipelining http requests. I had to tweak Firefox for higher parallelism (network.http.max-*) and pipelining (network.http.pipelining*) to achieve the speed reported above but it's been working like a charm since I did that.

My question is: how can I configure Konqueror (and kio_http in general) to use more parallel requests per host? Right now it's using 2 or 4, and I really need 100 or more. Can I enable HTTP pipelining and configure the number of pipelined requests? Can I do that for proxy/direct connections selectively?

Any help greatly appreciated!

Thanks,
Peter

---

