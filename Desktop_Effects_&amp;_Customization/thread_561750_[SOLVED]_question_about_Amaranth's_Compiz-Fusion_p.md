---
title: "[SOLVED] question about Amaranth's Compiz-Fusion packages"
date: 2007-09-27
forum: Desktop Effects &amp; Customization
---

### Post by erfahren on 2007-09-27
a few weeks ago I followed [the guide that was here]("http://ubuntuforums.org/showthread.php?t=481314) to remove Trevino's Compiz-Fusion packages and install Amaranth's.

The repositories given in that guide were:
deb [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse
deb-src [http://ppa.dogfood.launchpad.net/amaranth/ubuntu](http://ppa.dogfood.launchpad.net/amaranth/ubuntu) feisty main restricted universe multiverse

The HowTo part of the thread was removed later and it seemed the packages were no longer being updated. It also had a link to Amaranth's Ubuntu Community Documentation page regarding his packages, but I didn't bookmark it.

It seemed that some were having problems with the packages which I thought might have been why the HowTo was removed and the thread was closed. They seemed to be working well for me though, (aside from the "update when there was no update bug" - easily fixed by commenting the repositories out when not needed.) Whatever the case I decided to just let it go until everything was sorted out.

Anyway, I just noticed in another thread a link to a [blog post](http://forlong.blogage.de/article/2007/8/26/The-best-way-to-install-Compiz-Fusion-on-Ubuntu-Feisty) giving these as Amaranth's packages:
deb [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main
deb-src [http://ppa.launchpad.net/amaranth/ubuntu](http://ppa.launchpad.net/amaranth/ubuntu) feisty main

So here's my question (finally): Are the packages the same in the later repositories as the ones in the original ones? In other words: would it be a problem for me to just change the links to the repositories in my sources.list and recieve the correct updates, or do should I purge and re-install them again?

---

### Post by hyperair on 2007-09-28
I reckon they are the same, just a later version in the Launchpad repository. After all, the packages were gotten from the same place (i.e. Gutsy)

---

### Post by Forlong on 2007-09-28
> **erfahren said:**
> So here's my question (finally): Are the packages the same in the later repositories as the ones in the original ones?
No, the packages in the new one are on par with up-to-date Gutsy.
The packages in the dogfoot one weren't updated in weeks.
> **erfahren said:**
> In other words: would it be a problem for me to just change the links to the repositories in my sources.list and recieve the correct updates, or do should I purge and re-install them again?
Just change the repository and install the available updates and you will be fine. Don't forget to disable it afterwards, because the update-issue with compiz-core still hasn't been fixed.

---

### Post by erfahren on 2007-09-28
Thanks! Got it updated and is working well. 

I thought that they would most likely work, but wanted to be more confident. (With an ATI video card anything to do with desktop effects starts to seem a little precarious!)

thanks again

---

