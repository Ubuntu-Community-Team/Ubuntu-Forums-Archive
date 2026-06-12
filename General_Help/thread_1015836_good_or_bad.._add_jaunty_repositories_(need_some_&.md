---
title: "good or bad.. add jaunty repositories (need some &gt;8.10 modules) to intrepid install?"
date: 2008-12-19
forum: General Help
---

### Post by zim2dive on 2008-12-19
I need to upgrade my nvidia driver to 177.82 for hdmi sound.

It is perfectly easy to do this thru several command line steps, but I note that this driver is also already available in the jaunty repository... so it occurred to me that maybe I could install it that way.. or would that be a path that would lead me to many many headaches?

(I also need the newer alsa version)

I'm new to Ubuntu and repositories, so I didn't know how well (or even if) having both intrepid and jaunty repositories in my list would co-exist.

thanks,
Mike

---

### Post by taurus on 2008-12-19
Nobody can stop you from adding another repo from another release to your /etc/apt/sources.list but chances are your machine will break.  Of course, you can always try out jaunty.

---

### Post by zim2dive on 2008-12-19
> **taurus said:**
> Nobody can stop you from adding another repo from another release to your /etc/apt/sources.list but chances are your machine will break.  Of course, you can always try out jaunty.

I know no one can stop me :)  I just didn't know if "mixing" was a guaranteed bad idea.

Call this a chemistry experiment, and folks here being expert chemists.. I have 2 compounds I want to mix... are they going to blow up, or do they mix well within certain guidelines?

(ie. would the installs I get be compiled against different headers/libraries?)

---

### Post by FuturePilot on 2008-12-19
> **zim2dive said:**
> 
(ie. would the installs I get be compiled against different headers/libraries?)

Yes. And chances are, more likely than not, that doing so will break something.

---

### Post by zim2dive on 2008-12-19
> **FuturePilot said:**
> Yes. And chances are, more likely than not, that doing so will break something.

Ok, thanks.. I'll stick to doing the installs by hand.

Newbie question: Will these newer versions work their way into the 8.10 repositories at some point?  Or are the repositories static for any given release? (I don't yet understand how that cycle works)

thanks!

---

### Post by FuturePilot on 2008-12-19
> **zim2dive said:**
> Ok, thanks.. I'll stick to doing the installs by hand.

Newbie question: Will these newer versions work their way into the 8.10 repositories at some point?  Or are the repositories static for any given release? (I don't yet understand how that cycle works)

thanks!
You're welcome!

No, the new versions won't go into the current release. At release time, the repositories are frozen. The only possibility for a new version to make it in is through the "backports" repository.

---

### Post by zim2dive on 2008-12-19
> **taurus said:**
> Of course, you can always try out jaunty.

Mildly puzzled that the repositories won't see these post-8.10-release drivers, given that the jaunty alpha comes with warnings of "don't use if you expect a stable system"? (I'm probably will to take that risk)

Again, I'm new to this, so I don't yet comprehend the way the cycle works.. but had (wrongly) assumed Intrepid would see updated items appear in its repositories until jaunty was an official release... ie, when VLC makes a new release, it would never make it into the Intrepid repositories?  (maybe I am mis-comprehending what I've read so far.. tho I will guess this is a decision arrived at after many long & philosophical discussions which were often "spirited" ;) )

Just trying to get a basic understanding of how thing work.

thanks again,
Mike

---

### Post by FuturePilot on 2008-12-19
> **zim2dive said:**
>  ie, when VLC makes a new release, it would never make it into the Intrepid repositories?  


Correct, unless like I said before, the backports team decides to backport a newer version to the current stable release of Ubuntu. The reasoning behind freezing the repositories is that there is much less of a chance of regressions and breakage from updates. Though some may disagree with this theory of time based releases, which has been debated many times between the people that agree with time based releases and rolling releases. Some Linux distros out there are rolling releases meaning that as soon a new version of something is released, you get it immediately. Though both philosophies have their advantages and disadvantages.

---

### Post by zim2dive on 2008-12-19
> **FuturePilot said:**
> Correct, unless like I said before, the backports team decides to backport a newer version to the current stable release of Ubuntu. The reasoning behind freezing the repositories is that there is much less of a chance of regressions and breakage from updates. Though some may disagree with this theory of time based releases, which has been debated many times between the people that agree with time based releases and rolling releases. Some Linux distros out there are rolling releases meaning that as soon a new version of something is released, you get it immediately. Though both philosophies have their advantages and disadvantages.

Understood.. thanks for helping me learn.

---

### Post by philinux on 2008-12-19
> **zim2dive said:**
> I need to upgrade my nvidia driver to 177.82 for hdmi sound.

It is perfectly easy to do this thru several command line steps, but I note that this driver is also already available in the jaunty repository... so it occurred to me that maybe I could install it that way.. or would that be a path that would lead me to many many headaches?

(I also need the newer alsa version)

I'm new to Ubuntu and repositories, so I didn't know how well (or even if) having both intrepid and jaunty repositories in my list would co-exist.

thanks,
Mike

Better idea would be to temporarily enable the proposed repos. That driver is in the list of updates. Since it's in proposed it's only a matter of time/testing before it appears through the backports.

---

### Post by lswb on 2008-12-19
Using a non-standard repository can work for user application programs but drivers and other lower-level binaries usually need to be compiled to work with a specific kernel. You may have noticed how a kernel update always brings in a new driver directory tree.

---

### Post by zim2dive on 2008-12-19
> **lswb said:**
> Using a non-standard repository can work for user application programs but drivers and other lower-level binaries usually need to be compiled to work with a specific kernel. You may have noticed how a kernel update always brings in a new driver directory tree.

Actually no, I just installed Intrepid less than 2 weeks ago, and its my 1st home install of any distro (I've used various flavors of *nix at work for 15+ years, but 1st time I'm learning my way around and how the various releases work)... so adding repositories, backports, etc, is all new to me.  I'm decently competent once I understand something, but often benefit from small words :)

---

