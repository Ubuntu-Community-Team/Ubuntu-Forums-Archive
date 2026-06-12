---
title: "Sword and Sworcery installation error"
date: 2013-07-07
forum: Gaming &amp; Leisure
---

### Post by Cerapter on 2013-07-07
I've been messing around for a few days trying to install this game after buying it through Ubuntu One. I've tried to contact the developer, but I've not gotten a response yet. Maybe somone could point me in the right direction?

This is what happens when I try to install the game, after adding the key and ppa:
```
cerapter@Ancalagon:~$ sudo apt-get install swordandsworcery
[sudo] password for cerapter: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  swordandsworcery-bin:i386
The following NEW packages will be installed:
  swordandsworcery swordandsworcery-bin:i386
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
**Need to get 325 MB of archives.**
After this operation, 337 MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Get:1 [https://private-ppa.launchpad.net/commercial-ppa-uploaders/swordandsworcery/ubuntu/](https://private-ppa.launchpad.net/commercial-ppa-uploaders/swordandsworcery/ubuntu/) precise/main swordandsworcery-bin i386 1:1.02-0ubuntu1 [325 MB]
100% [1 swordandsworcery-bin 368 MB/368 MB 100%]                               
Get:2 [https://private-ppa.launchpad.net/commercial-ppa-uploaders/swordandsworcery/ubuntu/](https://private-ppa.launchpad.net/commercial-ppa-uploaders/swordandsworcery/ubuntu/) precise/main swordandsworcery amd64 1:1.02-0ubuntu1 [16.2 kB]
**Fetched 383 MB in 38min 12s** (167 kB/s)                                         
Failed to fetch [https://private-ppa.launchpad.net/commercial-ppa-uploaders/swordandsworcery/ubuntu/pool/main/s/swordandsworcery/swordandsworcery-bin_1.02-0ubuntu1_i386.deb](https://private-ppa.launchpad.net/commercial-ppa-uploaders/swordandsworcery/ubuntu/pool/main/s/swordandsworcery/swordandsworcery-bin_1.02-0ubuntu1_i386.deb)  Size mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

None of the suggestions seem to work. I've also tried to install the package swordandsorcery-bin, with the same result, although a different file size that time.

I'm on 12.04 LTS, 64 bit version. I don't use Steam and I haven't bought the game through the Humble Indie Bundle.

---

### Post by Ranko Kohime on 2013-07-08
I've never seen that before.

The PPA requires a user/pass, (I presume because the game is a pay game), so I can't try this myself, but my suggestion is to try going to the directory in a web browser, and downloading the file in the web browser, and see what it does.

If you can download the .deb successfully, then just drop it in _/var/cache/apt/archives_, then try installing it again.

ETA: It looks like both did the same thing, too, so download both files.

---

### Post by Cerapter on 2013-07-15
I successfully installed the game in the end. I do not fully understand how. I can only guess this: the 19% that was downloaded on the first unsuccessful attempt, was not brought from the cache, but this was downloaded all over again which added to the total file size.

It worked after I did all the cache and list clearings I could muster, then an update, and then try again. I might have failed to do this thoroughly earlier, as I was on a slow connection and my apt-get update would take a long time.

---

