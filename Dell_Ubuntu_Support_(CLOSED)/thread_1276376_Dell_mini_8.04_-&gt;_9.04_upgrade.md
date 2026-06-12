---
title: "Dell mini 8.04 -&gt; 9.04 upgrade"
date: 2009-09-27
forum: Dell Ubuntu Support (CLOSED)
---

### Post by michael37 on 2009-09-27
I noticed that Ubuntu 9.04 is now available in the dell mini lpia flavor from canonical site: [http://dell-mini.archive.canonical.com/updates/dists/jaunty-dell-mini/](http://dell-mini.archive.canonical.com/updates/dists/jaunty-dell-mini/)

Does anyone know how to upgrade from 8.04 to 9.04?  Update-manager (incl. -d) is not helping.

Given that I have Dell Mini 12 with GMA 500 video, I got to stay lpia.

---

### Post by wangnk on 2009-09-27
No official way for Dell image from 8.04 to 9.04. But you can install UNR 9.04 on Dell mini 9 and 10v system...just losing some Dell special application.

BTW, UNR 9.04 may not support Dell mini10 and mini 12 which are lack of GMA500 driver on Jaunty.

---

### Post by michael37 on 2009-09-27
> **wangnk said:**
> No official way for Dell image from 8.04 to 9.04. But you can install UNR 9.04 on Dell mini 9 and 10v system...just losing some Dell special application.

AFAIK, UNR would wipe my disk.  Is there a way to upgrade rather than a clean install?

> **wangnk said:**
> 
BTW, UNR 9.04 may not support Dell mini10 and mini 12 which are lack of GMA500 driver on Jaunty.
Yeah, I am well familiar with the good work by ubuntu-mobile PPA team.  Looks like they really made it possible to use Jaunty UNR on GMA500.  I wonder if there are compatibility issues between their PPA and Dell-Canonical version of 9.04.

---

### Post by jwaclawsky on 2009-09-27
I have a Dell Mini 9 which I got with 8.04. I left the Dell Ubuntu distribution and just used Ubuntu 9.04. I copied and backed up my email client and browser bookmarks etc. by copying my .mozillia and .mozilla-thunderbird directories and document, pictures and music directories and just did a clean install and 9.04 is much better than 8.04 and the Dell mods. I recommend 9.04. I also found Dell wasn't any help if you had any Ubuntu issues (pretty clueless). In my case I wanted to move away from the crappy maximus program that Dell included in 8.04.

---

### Post by Greyed on 2009-09-27
> **michael37 said:**
> AFAIK, UNR would wipe my disk.  Is there a way to upgrade rather than a clean install?

It doesn't.  It gives the option of repartitioning the disc which includes shrinking the existing install.  I went through the UNR install a few weeks ago.  I've got Dell's 8.04 and UNR 9.04 on my 10v.

> Yeah, I am well familiar with the good work by ubuntu-mobile PPA team.  Looks like they really made it possible to use Jaunty UNR on GMA500.  I wonder if there are compatibility issues between their PPA and Dell-Canonical version of 9.04.

With the above said, and even with this, I would not recommend UNR 9.04.  I decided tonight to give up on it for several reasons.  Usability just declines from a decent experience to one with little annoyances.  What I gained in no way offset those annoyances.  I'd love to get a 9.04 update from Dell, one which is as solid and smooth as their 8.04 release.

---

### Post by michael37 on 2009-09-29
Which Dell 9.04 are you talking about?  Is it 9.04 i386 that is provided by linux.dell.com or 9.04 lpia that is posted on canonical.com ([http://dell-mini.archive.canonical.com/updates/dists/)?](http://dell-mini.archive.canonical.com/updates/dists/)?)

---

### Post by michael37 on 2009-09-29
Btw, I just upgraded my Dell Mini 12 (shipped with Dell-Canonical 8.04) to **Canonical 9.04 lpia**.  Upgraded as in sudo apt-get dist-upgrade, and not reinstall.

Took me half a day with a little bit of frustration, but it's been working charmingly well for the past several hours.  Stability is excellent so far.

Anyone interested?

---

### Post by Greyed on 2009-09-30
Well, given that these forums are archived and easily searchable I'm sure someone, sometime, will be interested.  :P

---

### Post by michael37 on 2009-09-30
> **Greyed said:**
> Well, given that these forums are archived and easily searchable I'm sure someone, sometime, will be interested.  :P

Umm, that may be a problem.  I can assure you that the chances of an upgrade working for an expert user is about 75%; the chance of the upgrade working for an average user is about 25%.   Posting this info online is inviting someone to mess up their ubuntu beyond repair :)

---

