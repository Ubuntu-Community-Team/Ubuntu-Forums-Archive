---
title: "VegaStrike Installation"
date: 2010-07-11
forum: Gaming &amp; Leisure
---

### Post by Thomas_Bates on 2010-07-11
I have found no other thread which sorts this out.
I'm using Ubuntu 10.04, and have recently revamped it to mimic LCARS, from my theme to my splash screens, and login. So, naturally, I wanted some games. I have StarVoyager, which is good, but I can't figure out how to get credits (guide anyone, google doesn't show one). NETrek, is eh, not good enough. I saw VegaStrike, which is awesome looking on its own, has a Trek mod. At this point, the MOD is w/e, but I want this game. All guides I've seen say to go into Synaptic and install the packages:
> vegastrike
vegastrike-data
vegastrike-music

I have DATA, and Music, but the "vegastrike" package is simply not there. I found this rather odd, but I can't find it anywhere. I tried
```
aptitude search vega
```
which showed data and music, but no pack for the actual game.

Can someone please help me? I know my post has been rather general, but I'm afraid I don't know what to post. If you need specific data, please ask. I really want to be able to play this.

---

### Post by Thomas_Bates on 2010-07-11
I figured it out, I overlooked something incredibly stupid.

---

### Post by kombipom on 2010-07-15
Which was?

---

### Post by Thomas_Bates on 2010-07-15
I went to the actual site, grabbed the SVN packs, and compiled it myself.

---

### Post by Siljrath on 2010-07-15
i encountered the same issue.    vegastrike is actually supposed to be there isnt it?  worth a bug report ya think?   or are we just expected to go get the latest source?



tangent,
i'd love to see your lcars screenshots / configs and whatever.  got a link to that somewhere?

---

### Post by Thomas_Bates on 2010-07-15
Well, because both the Data and Music packs are there, yes, I would assume it is a bug. However, the source that was in the repositories was outdated anyway, hopefully if it is re-added, they add the latest.

---

### Post by rCXer on 2010-07-15
> **Siljrath said:**
> i encountered the same issue.    vegastrike is actually supposed to be there isnt it?  worth a bug report ya think?   or are we just expected to go get the latest source?



tangent,
i'd love to see your lcars screenshots / configs and whatever.  got a link to that somewhere?

Yeah, vegastrike package has been removed from Ubuntu.  Look at [this](https://bugs.launchpad.net/ubuntu/+source/software-center/+bug/495203/comments/6) bug report comment.  I also think it would be worth it's own bug report (anybody want to submit one?).  Look at [this bug report]("https://bugs.launchpad.net/ubuntu/+source/vegastrike-data/+bug/403698") as well.

---

### Post by michaelwheatland on 2010-08-04
I am not good with compiling software. I am just an end user and love the deb format.

Does anyone know if there is a location where I can download a deb package for Vegastrike? I know if has been left out of the ubuntu repositories, but surely there is another repository which has the deb or even a location to download it.

Thanks.

---

### Post by Thomas_Bates on 2010-10-05
There isn't currently a .deb for VegaStrike's latest version.

---

