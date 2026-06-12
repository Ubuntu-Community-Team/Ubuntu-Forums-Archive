---
title: "Why is Firefox 1.5 a memory hog?"
date: 2005-12-14
forum: Desktop Environments
---

### Post by mcescher on 2005-12-14
I have wondered why when I use Firefox 1.5 to browse the net it is so slow to respond.

I have cable internet so my internet speed is not a problem.

I checked system resources and after rebooting my pc and only starting FIrefox it uses almost 50% of my computer resources just sitting idle on my home page?

What's the deal? Anyone have any suggestions or can tell me how to roll back to the basic version if it performs any better?

---

### Post by aysiu on 2005-12-14
I posted the same question a week ago:
[http://www.ubuntuforums.org/showthread.php?t=99052](http://www.ubuntuforums.org/showthread.php?t=99052)

---

### Post by dtfinch on 2005-12-14
After some searching, it turns out you can configure the maximum amount of ram it'll use for its memory cache, rather than letting it choose automatically based on your total ram. You have to go to about:config, create a new value called "browser.cache.memory.capacity", and set it to maximum number of kilobytes you want it to use for caching in ram. I don't think the memory cache is supposed to get much above 64mb though, no matter how much ram you have.

I myself haven't had a problem with FireFox's memory usage, aside from the old problem of it rarely shrinking below its peak usage. I had a lot of performance problems with 1.0.x. Most pre-1.0 releases were fine.

I have 36 tabs open (several forum tabs, and I middle clicked everything on Google's "more" page), and I viewed each one to ensure they're fully loaded into memory. According to System Monitor, Firefox is taking 133mb. That seems pretty high, but it also says even X is taking 174mb, which I know is far more than it needs. Then there are a couple dozen other programs that it says are taking 20-50mb each. Combined, this is easily double my total ram, but then on the next tab it says I'm using only half of my total, and zero swap. The System Monitor is somewhat misleading. Whenever I run a Windows program using wine, no matter how trivial, it says it's using 1.6gb, which is true in the sense that it allocated 1.6gb, but that's not how much the system has really given it. What really matters is the RSS value, which is how much ram is actually given to the program rather than how much it allocated for itself. According to the RSS values, Firefox is really using only 69mb and X is using only 42mb, both fairly reasonable amounts.

Have you tried other browsers to verify that FireFox is the cause of the slowness? My own cable connection gets really crappy at times. Most days it's perfect, but some days, or sometimes for a week at a time, dns queries take 5 seconds, ping packet loss is 50%, and ping lag is 2 seconds. I'm in a small town where there seems to be only one non-satellite high speed provider.

---

