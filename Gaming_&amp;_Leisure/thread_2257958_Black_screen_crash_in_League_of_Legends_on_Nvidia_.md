---
title: "Black screen crash in League of Legends on Nvidia driver"
date: 2014-12-23
forum: Gaming &amp; Leisure
---

### Post by michael241 on 2014-12-23
Hi people of these forums,

I have a problem when playing League of Legends on my ubuntu 14.04 LTS installation on my old ABook laptop.
It's installed using the PlayonLinux method, and besides my problem, runs perfectly.
When i get ingame, around 20 seconds pass and i get a black screen crash, nothing happens, nothing responds, no sound. I have to do a hard reboot.
If i continually alt-tab out and in i can also delay the crash indefinitely (while checking temperatures), but this makes it unplayable of course.
This is when using any of the Nvidia drivers in "Additional drivers".

When i use the X.org X Server - Nouveau display driver, i have no problems, but i have crappy performance (30 fps instead of 60+).

I thermal tested my laptop, both on CPU and GPU, can't get either to go over 83 degrees celcius. And nothing happened during stress-testing.
So it's not a thermal issue, game doesn't take the CPU or GPU over 60 degrees.

My laptop is an old ABook multimedia laptop - model 1785WII

Core2Duo 2.5 GHZ
4 Gigs of ram
Nvidia GT 130m 512 MB ram.
Ubuntu 14.04.1 LTS running UNITY, fresh install 1 day ago.

Any drivers that might perform better and not give me this issue?
I'm a noob regarding ubuntu, so i have no clue about what logfiles you might want, please let me know.

EDIT: Also, other games (both 2D and 3D) work fine with the Nvidia driver. I tried with awesomenauts, don't starve and Counter Strike GO, all from steam.

Could be a problem with TDR-delay, as seen [here]("http://support.microsoft.com/kb/2665946"), but i can't try the method as the same registry is not present in the wine registry database for my virtual drive.
I also can't find any version of wine that will start LoL in win7 compatibility instead, so i cannot check if it's a winxp emulation issue with my laptop/with wine.

Anybody out there with some kind of idea of something i could try? going a bit nuts over this issue.

EDIT2: Okay so it's definitely a so called thermal shutdown, but the sensors i have access to (1 for GPU i believe, and 2 for the cores) don't seem to go over 65 degrees in any way (except the stress testing i did for the GPU). Can it be a hidden sensor or an inaccessible internal one that might be faulty and reporting higher temperatures? The laptop doesn't feel warm enough to justify a thermal shutdown.

I have reason to believe it might be CPU related, since the stress-testing of the GPU did nothing, even at around 85 degrees.

It also happened after about 30 minutes in Dota 2.

LAST EDIT I'LL EVER DO: Did some CPU and Ram stresstesting, couldn't get my laptop to do anything else but perform without fault. I've given up now. It makes no sense to me.

---

