---
title: "No KDE 4.7.1 on Kubuntu backports for natty?"
date: 2011-09-08
forum: Desktop Environments
---

### Post by sonnet on 2011-09-08
As per title, I wanted to know if there was goona be a kde 4.7.1 update for jubuntu backports repository..
Softpedia article wrote it was already there into the repository the update, but I couldn't find it
[http://news.softpedia.com/news/KDE-SC-4-7-1-Is-Available-for-Download-220716.shtml](http://news.softpedia.com/news/KDE-SC-4-7-1-Is-Available-for-Download-220716.shtml)

---

### Post by lykwydchykyn on 2011-09-08
> **sonnet said:**
> As per title, I wanted to know if there was goona be a kde 4.7.1 update for jubuntu backports repository..
Softpedia article wrote it was already there into the repository the update, but I couldn't find it
[http://news.softpedia.com/news/KDE-SC-4-7-1-Is-Available-for-Download-220716.shtml](http://news.softpedia.com/news/KDE-SC-4-7-1-Is-Available-for-Download-220716.shtml)

Typically the point releases get added, though sometimes it takes a day or two for everything to compile and pass muster.

---

### Post by sonnet on 2011-09-13
mm ..still not there :(

---

### Post by 2F4U on 2011-09-13
I guess that the developers are busy integrating it into the upcoming release and may therefore put less effort into backporting it. Thats why it probably takes longer until it arrives.

---

### Post by lykwydchykyn on 2011-09-13
> **2F4U said:**
> I guess that the developers are busy integrating it into the upcoming release and may therefore put less effort into backporting it. Thats why it probably takes longer until it arrives.

I'd guess that as well, though I'm a bit disappointed; usually they stay on top of these releases pretty well.

---

### Post by dniMretsaM on 2011-09-13
It'd be nice, but I'm content waiting for 11.10. It'll come eventually.

---

### Post by hasinasi on 2011-09-17
For me, the work of the KDE folks did not work out so well. I had added the backports to my repos, because it gave me the monthly upgrades of KDE 4.6.x, each of which removed more bugs and got more stable.  

I wish the KDE packagers would have skipped 4.7.0, as it is in my experience more buggy than 4.6.5 (several kwin glitches, for instance). This is actually not so surprising for a .0 release. I just wish they would have instead directly moved to 4.7.1. It would have probably been a similar amount of work, but more satisfaction for the user in the end. I was looking for reliability and not for "bleeding edge". 

Now, I am stuck with 4.7.0 and can't go back. So let's hope 4.7.1 will eventually be added. And no, I am not looking forward to switching everything yet again to Oneiric. I know that's fun when one has enough extra time on his hands, but I don't. And so far there hasn't been a single release since Edgy in which there wasn't stuff broken after the upgrade. Eventually I found fixes or workarounds for everything in all cases. It's just time consuming and annoying. I used to enjoy this kind of stuff, but now I just don't have the time any more...

---

### Post by jim.hitch on 2011-09-21
> **hasinasi said:**
>  I was looking for reliability and not for "bleeding edge". 

Now, I am stuck with 4.7.0 and can't go back. So let's hope 4.7.1 will eventually be added. And no, I am not looking forward to switching everything yet again to Oneiric. I know that's fun when one has enough extra time on his hands, but I don't. And so far there hasn't been a single release since Edgy in which there wasn't stuff broken after the upgrade. Eventually I found fixes or workarounds for everything in all cases. It's just time consuming and annoying. I used to enjoy this kind of stuff, but now I just don't have the time any more...

If you're looking for reliability not 'bleeding edge' then you shouldn't have the backports added. I have little time for all this as well, but I'm conscious that there is a trade off between wanting the latest release and having a less stable system. 

You have plenty of choices if you want something more reliable and to have to add fixes etc. At the extreme end you could go for pure Debian Squeeze which I hear is as solid as a rock, or just go for the latest LTS release of Kubuntu (10.04), then you won't have to keep 'fiddling' until the next LTS comes. But if you want to have the latest, do what you do at the moment, but expect problems.

Personally I think everything above and including 4.6.5 has been excellent and is finally taking us back to what we had with 3.5.10. It's been a long road but worth it. I have been toying with going to Debian 6.0.2.1, for stability, but it's based on KDE 4.4.5 which is nowhere near as good as 4.7.x, so I have decided to stick with Kubuntu, and expect a few issues.

---

### Post by dniMretsaM on 2011-09-21
> **hasinasi said:**
> And so far there hasn't been a single release since Edgy in which there wasn't stuff broken after the upgrade. Eventually I found fixes or workarounds for everything in all cases. It's just time consuming and annoying. I used to enjoy this kind of stuff, but now I just don't have the time any more...

The fact that your upgrading is probably a large component of why you're system breaks. For one thing, updates usually break things, especially when there is a large structural change within the system (11.10 will be one of these releases I believe). Another thing is that if you've upgraded every time since Edgy, you probably have a ton of excess configuration files, etc. That clogs up a system fast. Go for a clean install. And if you're really looking for stability, stay with LTS versions. Or Debian Stable which is really, well, stable. And it's rolling release, which removes a lot of the upgrade problems (I personally wouldn't be unhappy if Ubuntu moved to this).

---

### Post by sumski on 2011-09-23
[https://lists.ubuntu.com/archives/kubuntu-devel/2011-September/005522.html](https://lists.ubuntu.com/archives/kubuntu-devel/2011-September/005522.html)

---

### Post by jim.hitch on 2011-09-23
Thanks Sumski.

---

### Post by hasinasi on 2011-09-25
> **sumski said:**
> [https://lists.ubuntu.com/archives/kubuntu-devel/2011-September/005522.html](https://lists.ubuntu.com/archives/kubuntu-devel/2011-September/005522.html)

@sumski: Awesome! Thanks for letting us know!

---

### Post by hasinasi on 2011-09-25
> **dniMretsaM said:**
> The fact that your upgrading is probably a large component of why you're system breaks. For one thing, updates usually break things, especially when there is a large structural change within the system (11.10 will be one of these releases I believe). Another thing is that if you've upgraded every time since Edgy, you probably have a ton of excess configuration files, etc. That clogs up a system fast. Go for a clean install. And if you're really looking for stability, stay with LTS versions. Or Debian Stable which is really, well, stable. And it's rolling release, which removes a lot of the upgrade problems (I personally wouldn't be unhappy if Ubuntu moved to this).

@dniMretsaM: 

I guess I wasn't very accurate in my description. I completely agree with you that upgrades are questionable. And that's why I never do them. So when I said "upgrading" I actually meant doing a clean install of the latest OS (I have scripts to install all the packages I want and to do some of my preferred settings, which saves a lot of time). Still, there are always lots of little details and quirks which need to be figured out individually in each version of kubuntu... 

And yes, I actually installed the lucid LTS and planned on keeping it (I had actually skipped Maverick). Now, it's just started to be a bit dated. I am actually not so much after the OS updates, for me it matters more to have more recent versions of the apps. 

I also recently tried to install Debian, but I found it was much less straightforward to get it working. I don't remember exactly what it was, but there were some problems, and altogether, it didn't look like it could be made to "just work" with a few little tricks...

---

### Post by hasinasi on 2011-09-25
All:  

I just did an "dist-upgrade" on my machine and found that 4.7.1 is now in the repo! Awesome! Thanks to all.

---

