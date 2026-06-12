---
title: "The Evolution of Desktop Environments"
date: 2018-05-08
forum: Desktop Environments
---

### Post by deanr2 on 2018-05-08
I'm currently running (on this machine, at least) Ubuntu Mate 16.04. Probably like many users I'm interested in the upgrade to a newer version but I've read somewhere that I shouldn't, for example, upgrade from 16.04 to 17.10 but rather wait until 18.04.1. Fair enough. But...

Isn't 17.10 just a later version of 17.04, which is a later version of 16.10, which is a later version of 16.04? Which in turn means that 18.04 is just an updated version of 17.10 that I'm being told to avoid?

So what's the big deal? Or is that not at all the way that each new version evolves from an older one to a newer one?

---

### Post by hier-kommt-luis on 2018-05-08
Well, yes, there's no huge difference between these version at first glance. Except the one that the versions with 10 are may be unstable and have 3-month support cycle, when 4's are safer and supported for years

---

### Post by PaulW2U on 2018-05-08
> **hier-kommt-luis said:**
> Well, yes, there's no huge difference between these version at first glance. Except the one that the versions with 10 are may be unstable and have 3-month support cycle, when 4's are safer and supported for years
Not quite. All releases are supported for nine months except the .04 LTS release of even years. An Ubuntu LTS will be supported for five years but a flavours LTS such as Kubuntu for only three years. I wouldn't say that some releases are unstable though but they may have introduced significant changes that require more testing and further development. The LTS releases will have more conservative changes than other releases but generally all software is updated in line with what is in Debian Testing during the development phase of each release.

Some flavours will appear to have more changes than others especially when the desktop changes like it did recently with Ubuntu and also did with Kubuntu when they moved from KDE4 to Plasma 5.

---

### Post by QIII on 2018-05-08
:)

Kubuntu LTS releases are supported for five years.

Xubuntu gets 3 years of support.

That's not a hard and fast rule.  The communities supporting the flavors can decide how long to support their versions.  Sometimes they have even skipped an LTS release altogether.

---

### Post by PaulW2U on 2018-05-08
> **QIII said:**
> Kubuntu LTS releases are supported for five years.
Not according to their [Release Notes]("https://wiki.ubuntu.com/BionicBeaver/ReleaseNotes/Kubuntu") although it may have been five years in the past. As you say each of the community supported flavours decide how long to support their LTS release but they generally decide on three years now.

---

### Post by rsteinmetz70112 on 2018-05-08
Official Ubuntu LTS versions are released every 2 years in April (more or less) of even numbered years. 16.04 LTS was the last version. 18.04 LTS is the latest version Automated upgrades for 16.04 LTS will be available when 18.04.1 LTS is released in a few months if you checked the box in Update Manager settings to only show you LTS version upgrades. The reason for the delay is so that any glitches in the new version can be worked out before upgrading systems running LST versions since people doing that are generally interested in stability more than bleeding edge.

I only use Ubuntu LTS versions because I don't want to be upgrading all of the time.

---

### Post by deadflowr on 2018-05-08
> Isn't 17.10 just a later version of 17.04, which is a later version of 16.10, which is a later version of 16.04? Which in turn means that 18.04 is just an updated version of 17.10 that I'm being told to avoid?

So what's the big deal? Or is that not at all the way that each new version evolves from an older one to a newer one?
Upgrading to a release that will only last a couple more months now does not seem worth it as you'll soon need to upgrade that again.
Easier to wait it out and skip that release and go directly to the next longer supported release.

I think it's been posted the difference between long term supported releases and the standard non-lts releases.
I would recommend that if you wanted to run the non-lts releases, it would be preferable to install them relatively close to their respected release dates.
Simply so you can get the most out of it.

Also packages can change (some minor some major) between releases.
So it's not really a case of one version being a just newer version versus the last version.
It's more of this version has these features, and that version will have those features.
You'll find, even with very stable Desktop flavors, things can be in constant flux and ever evolving.

---

### Post by #&amp;thj^% on 2018-05-08
And to add, bear in mind evolutionary dose not always mean revolutionary. :)

---

### Post by deanr2 on 2018-05-09
[B][I][COLOR=#000000]

Upgrading to a release that will only last a couple more months now does not seem worth it as you'll soon need to upgrade that again.[/COLOR][/I][/B]

Yeah, but this is kinda why I asked. 

If each consecutive release is based on a previous one and will go on form the basis of the next one, apart from the hassle of doing a clean install (and let's imagine we're just upgrading via the software updater GUI), I don't see why this should actually matter...

---

### Post by tinylagarto on 2018-05-10
It matters because in some cases the upgrade goes wrong. Or you have a workstation and you really need it to be an appliance and do not want to bother with upgrades every six months. In a corporate environment this matters! 

Upgrading from release to release is possible but not really tested whereas from one LTS to another might already be the case, therefor waiting until the first point release (18.04.1).

---

