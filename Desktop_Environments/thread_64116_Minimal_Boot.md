---
title: "Minimal Boot"
date: 2005-09-09
forum: Desktop Environments
---

### Post by waynejkruse10 on 2005-09-09
I finnally got my server ticking with PHP and MYSQL and its serving IPB 1.3 at the moment nicely. Ubuntu has been a lovely Distro to work with on this project  :smile:. However when i get it actually doing stuff (serving a form via LAN) mabye ram and cpu will be wasted on the desktop environment. It has 384mb Ram and a 450mhz processor.

I know you can press CTRL-ALT-F5 or something to drop down to full screen terminal but the desktop enviroment is still in ram and chewing up cpu because you can easily switch back to it.

So, whats the most efficient way of running ubuntu for a server in text mode so the most amount of processor and ram is used on serving, Apache, MYSQL, PHP etc, and the least amount of resources are being hogged by other stuff.

---

### Post by heimo on 2005-09-10
If you still want to keep the desktop available, you could stop X environment and all the related stuff by running
 ```
sudo /etc/init.d/gdm stop
``` 

And if you want to make this the default behaviour after boot, you could change the default initlevel (2) symlink for gdm, like this:
 ```
sudo mv /etc/rc2.d/S13gdm /etc/rc2.d/K13gdm
``` 
(S=start, K=kill)

And instead of shutting down gdm when unneeded, you can now start it as neccessary:
 ```
sudo /etc/init.d/gdm start
``` 

Personally, I run my servers headless and administer with ssh and bash (command line). That's very convenient if you have slow connections and computers all over country. :)

---

### Post by waynejkruse10 on 2005-09-10
thanks, works great.

also, whats better for serving: P3 450 384mb Ram or P3 600 256mb Ram.

---

### Post by John Nilsson on 2005-09-10
[QUOTE=waynejkruse10]thanks, works great.

also, whats better for serving: P3 450 384mb Ram or P3 600 256mb Ram.[/QUOTE]

Only way to know is to benchmark with your particular app. More RAM menas more cache, which mens that it's more likley that you can just move data directly from ram to nic instead of having to read from disk.

More CPU means quicker processing of scripts, and requests.

One cold say that more RAM is good for latency, and more CPU is good for throughput.

In essence, if you have many requests but little data, go for CPU. If you have few requests but much data, go for RAM.

But still, benchmarking is the way to go.

---

