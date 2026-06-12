---
title: "Thoughts on Debian"
date: 2008-10-02
forum: Debian
---

### Post by Ozor Mox on 2008-10-02
I'd really like to get a Debian system up and running, and I've tried many times in VirtualBox to see how I get on. Trouble is, and I hope I'm not alone here, I like to run things that are stable and released, unless I specifically want to test new software that is still in alpha or beta. So the way I see it:

Ubuntu 8.04 is equivalent to Debian 4.0 stable, since they are both stable, official releases.

Ubuntu 8.10 beta is equivalent to Debian testing, since they are both somewhat tested versions of the next release.

Ubuntu 8.10 nightly builds or something is the equivalent to Debian unstable, since they both have mostly untested packages.

(I know Debian has an even more bleeding edge level of experimental, but I won't even go there :))

So I want to install Debian stable, which works beautifully and is rock solid, but has the outdated packages problem. Updating to testing from stable is meant to be easy, but I have done it several times and it will not boot from the new kernel that gets installed, only the old one.

Installing Debian testing directly works fine, but something irks me about using that as my desktop operating system. I want a nice released final version, the equivalent of what Ubuntu delivers every 6 months.

So, is it better to stick with a distribution like Ubuntu, intended to deliver Debian in a more up-to-date way? Should I just go for it with the Debian testing ISO? Is Debian stable enough? I'd still love to know where I'm going wrong when I update stable, unless maybe it is VirtualBox related?

I know this is kind of a pointless post, but I've always thought it would be nice to run Ubuntu's base, but never really been able to get my head around the best way to do it. I'd be interested to hear other people's thoughts and what they think of the versions of Debian.

---

### Post by kerry_s on 2008-10-02
debian stable is enough, but if you want bleeding edge debian try sidux:
[http://distrowatch.com/index.php?distribution=sidux&month=all&year=all](http://distrowatch.com/index.php?distribution=sidux&month=all&year=all)

i use debian etch and i'm perfectly happy, there's no surprizes, when i turn on the computer it always works.
i just did a fresh install this mourning.

---

### Post by Nikolai D. on 2008-10-02
Hi Ozor, and guys.

This is a question i've also been wondering about for some time. All i can tell you. I've came to an conclusion. It's my personal tough, and anyone is free to correct me if im wrong somewhere. But my impression is Debian testing is even stabler then Ubuntu LTS. Because Debian is all about stability. Debian is a name of an OS, which uses different kernels and runs on different architectures. This is only one GNU, Linux, GNU/Linux, or whatever you call it that is an OS not some another one vanilla distro derivative. I think Debian is todays Unix. :) GNU was an attempt to. Debian is an success of. Which combines best of the both worlds, GNU and Linux.

Why i say such a things. I've been using Ubuntu on my seven years old PC for two years or something like that. Tried Mint to, and some others. But Ubuntu was alweys the one for me. Thanks  to UbuntuForums, UbuntuWiki, and Ubuntu irc channel. Since i've bought a Mac(Mini). And i've did it only because i couldn't find better HW. I haven't used Linux for nearly a year anymore. Altrough i was planning to install Linux on it. And i've installed, but still i use OSX atm. But thats another topic.

While i was trying out virtual networking with virtual box, gnome hung. And i get it every time im out of ram. I have 1gig, just enough for two guests to run. XP and Server2003. I was planning long ago to try out Debian Testing. I just wanted first to get more knowledge of Linux. Because Debian is a little bit more technical i would say. You get all the explanation you want but you have to read. And keep digging in doc's. I was already pretty sure that Debian is serious system. But when i have read this article i've got a little bit more insight, or got a better picture of the branches, like testing and unstable and so.

Here's the link:
[http://www.horizonenergycorp.com/hpo/constellations/bible.htm](http://www.horizonenergycorp.com/hpo/constellations/bible.htm)

I advice you to read it, there are interesting thing there. Although the guy is right about maybe BSD being better from technical point of view. Linux is not that much about technical side of the medal but about the License. This is why Linux is popular and BSD isnt, while its maybe not bad at all.

Anyway. I wish a good reading to you. :)
I hope my english is ok.
Best wishes.
Nikolai

---

### Post by Ozor Mox on 2008-10-02
kerry_s, good point about sidux. I have tried it before and was impressed, though it would be nice if there was a GNOME version. I've tried to get the latest one working in VirtualBox, but it will not boot. Still, I will try burning it to a CD and running it live, and see if that works.

Nikolai, I don't get the link, but otherwise thanks. I've read several times that Debian testing is as stable as, if not more so, than many stable releases of other distributions. I guess if it was more of a 'proper' release I would be more inclined to use it, but it's that it is not provided like that on the Debian website that puts me off a little. Maybe this is unfounded, I don't know. Also your English is fine!

---

### Post by snowpine on 2008-10-02
Ubuntu is derived from Debian Sid. Debian Lenny is almost ready and will become the new stable version any day now, and I would say Lenny is probably more stable than Ubuntu 8.04 or 8.10 at this point. Debian Etch, there's just no comparison.

This is all just my opinion.

---

### Post by utUtu on 2008-10-02
Not sure about gnome, but my sid/KDE3 has been always stable and is my primary box, and experimental/KDE4 is pretty much stable.  I even run with nV 177.78 with no problem which I can't with 8.10.

---

### Post by p_quarles on 2008-10-02
> **Ozor Mox said:**
> Ubuntu 8.04 is equivalent to Debian 4.0 stable, since they are both stable, official releases.
No, they are not even roughly equivalent. "Stable" for Debian means that something has been put through a lot more quality control than an Ubuntu release. It is consequently both more reliable and less cutting edge. 

It is a common misconception that "LTS" releases (long term support) are somehow supposed to be the more "stable" Ubuntu releases, but that is not the case. All Ubuntu releases are bleeding edge and experimental from the perspective of the Debian development cycle.

---

### Post by Ozor Mox on 2008-10-03
> **p_quarles said:**
> No, they are not even roughly equivalent. "Stable" for Debian means that something has been put through a lot more quality control than an Ubuntu release. It is consequently both more reliable and less cutting edge. 

It is a common misconception that "LTS" releases (long term support) are somehow supposed to be the more "stable" Ubuntu releases, but that is not the case. All Ubuntu releases are bleeding edge and experimental from the perspective of the Debian development cycle.

I understand that, I realise that the two different approaches to what constitutes a 'stable' release are very different. I probably didn't explain myself well enough. I meant that Ubuntu 8.04 is equivalent to Debian 4.0 stable in the way that they are marked and released officially as stable versions. As I said, Debian testing or unstable may well be as stable as, if not more so, than a proper Ubuntu release, but they are not proper releases, they are the *equivalent* of running an Ubuntu alpha or beta release, in terms of status not stability.

My issue with this is that I like to run released things unless I'm testing stuff or experimenting, so my inclination is to go with the latest official Debian release (Etch). But I think with Debian, I am probably wrong in thinking like this, since the way it works is not quite like other distros, hence my difficulty in deciding on what to go with.

---

### Post by p_quarles on 2008-10-03
> **Ozor Mox said:**
> My issue with this is that I like to run released things unless I'm testing stuff or experimenting, so my inclination is to go with the latest official Debian release (Etch). But I think with Debian, I am probably wrong in thinking like this, since the way it works is not quite like other distros, hence my difficulty in deciding on what to go with.
The amount of stability you are going to get in a testing snapshot depends a lot on where it is in the development cycle. Right now, Lenny is in feature freeze and well on its way to a full release. There are relatively few reasons not to run it, and it will certainly support recent hardware to a much greater extent than Etch. For a desktop at this point, I don't see any advantage to Etch at all. 

Etch is more the equivalent of Ubuntu 6.06, in that its packages date to roughly the same time (a few months later, though, so includes Firefox 2).

---

