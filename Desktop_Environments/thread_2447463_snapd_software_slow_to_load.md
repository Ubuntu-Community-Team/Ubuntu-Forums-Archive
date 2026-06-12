---
title: "snapd software slow to load"
date: 2020-07-19
forum: Desktop Environments
---

### Post by oceanbottle on 2020-07-19
Hi,
I installed chromium that is a snapd software. And also leafpad that is a very light editor. But both are slow especially during loading. For example to open leafpad I need 7 seconds.
Why chromium is installed by snap ? And how can I make them  quick ?

---

### Post by Dennis N on 2020-07-19
The snap programs are stored in compressed files. These need to be decompressed to run, which takes a few seconds. If you close then relaunch in the same session, the time to opening is reduced in my experience.

---

### Post by CatKiller on 2020-07-19
> **oceanbottle said:**
> Why chromium is installed by snap ?

[https://ubuntu.com/blog/chromium-in-ubuntu-deb-to-snap-transition](https://ubuntu.com/blog/chromium-in-ubuntu-deb-to-snap-transition)

---

### Post by oceanbottle on 2020-07-19
As I know if I close something and I reopen it, it's more fast because it's already cached in ram.

---

### Post by TenPlus1 on 2020-07-31
I removed snap from my lubuntu system and install chromium browser from this source instead (chromium and chromium codecs) [https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage/+packages](https://launchpad.net/~canonical-chromium-builds/+archive/ubuntu/stage/+packages)

---

### Post by kurt18947 on 2020-07-31
> **Dennis N said:**
> The snap programs are stored in compressed files. These need to be decompressed to run, which takes a few seconds. If you close then relaunch in the same session, the time to opening is reduced in my experience.

I installed the Okular snap. The first time I launched it took 10 sec.+. The next time was instantaneous. Log out and back in still instantaneous. The only time I find snap app launch  a little slow is after a restart.

---

### Post by ActionParsnip on 2020-08-01
How long do they take to launch?

---

### Post by oceanbottle on 2020-08-09
@ 				 					[ 						 							[IMG]https://ubuntuforums.org/customavatars/avatar21486_2.gif[/IMG] 						 					]("https://ubuntuforums.org/member.php?u=21486") 				 				 					 						 	[**[COLOR=#000000]TenPlus1[/COLOR]**]("https://ubuntuforums.org/member.php?u=21486")
Yes, but there are a lot of app that now are in the snap store. For example cherrytree, leafpad, chromium, gtk themes.

@[URL="https://ubuntuforums.org/member.php?u=1447222"][B][COLOR=#000000]kurt18947
[/COLOR][/B][/URL]As I said the app is cached in ram then it's obvious that is more fast the second time.

@[**[COLOR=#000000]ActionParsnip[/COLOR]**]("https://ubuntuforums.org/member.php?u=1079078")
it take 2 or 3 times the time of original.

---

### Post by ActionParsnip on 2020-08-09
I see. TBH I use very few applications and most of my system use is in a terminal. It's interesting to see how people use and experience Ubuntu though. From what I've heard this is normal for the first run of snap apps.

---

### Post by CatKiller on 2020-08-09
> **oceanbottle said:**
> As I said the app is cached in ram then it's obvious that is more fast the second time.

It's not that the application is cached, which is true of all applications.

As far as the snapped application is concerned, it's running on a perfectly normal Ubuntu install. Even if it's being run on a different distro. Even if it's not running on Linux at all.

The setup of all the environment things that the application expects in its sandbox is what takes the time. The setup time for a relatively self-contained server application is much lower than for a graphical application that expects all kinds of libraries in particular places.

Not having to do all of that again is what saves the time on the second run.

---

### Post by kurt18947 on 2020-08-09
> **oceanbottle said:**
> @                                      [                                                      [IMG]https://ubuntuforums.org/customavatars/avatar21486_2.gif[/IMG]                                              ]("https://ubuntuforums.org/member.php?u=21486")                                                                                     [**[COLOR=#000000]TenPlus1[/COLOR]**]("https://ubuntuforums.org/member.php?u=21486")
Yes, but there are a lot of app that now are in the snap store. For example cherrytree, leafpad, chromium, gtk themes.

@[URL="https://ubuntuforums.org/member.php?u=1447222"][B][COLOR=#000000]kurt18947
[/COLOR][/B][/URL]As I said the app is cached in ram then it's obvious that is more fast the second time.

@[**[COLOR=#000000]ActionParsnip[/COLOR]**]("https://ubuntuforums.org/member.php?u=1079078")
it take 2 or 3 times the time of original.

It's not cached in RAM after a restart. I found Okular a *little* slower to launch after a restart than after logging out but not too much. The first time I launched it took the longest to start, longer than after a restart.

---

### Post by dino99 on 2020-08-13
By default there are two snap's copies installed: the last one and the previous one. This is to be able to roll back if needed; but it also disturb the system when loading a snap app, and you get chromium for example ( a snap app now) to load/open  very slowly. To resolve that problem , simply purge the old version.

[https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html](https://www.linuxuprising.com/2019/04/how-to-remove-old-snap-versions-to-free.html)

---

