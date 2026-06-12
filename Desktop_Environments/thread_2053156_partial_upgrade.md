---
title: "partial upgrade"
date: 2012-09-04
forum: Desktop Environments
---

### Post by houndhen on 2012-09-04
Installed 12.04.1 32 bit on my laptop and it works fine. I got a notification that I could do a partial upgrade. So I ran the partial upgrade. Everything seems fine still. I was thinking that the other part of the upgrade would be ready after re-booting. Questions:

1. What was being upgraded?
2. Is there more upgrade to follow?

Thanks,
Harold

---

### Post by doktorOblivion on 2012-09-04
Normally, your kernel and it's sources got upgraded and one would hope most of the applications you had installed.  However, I will admit, I have only had one absolute success with online upgrade where you push the button in synaptic.  Normally, I burn a DVD or CD-R.  However, having said that, what exactly are you concerned about?

---

### Post by QIII on 2012-09-04
I believe houndhen was talking about periodic updates, not a version upgrade.  Periodic updates are a normal, perfectly safe and prudent task on line.

My advice is to avoid partial upgrades and wait 24 hours before doing updates again.  Partial upgrades can cause problems up to and including completely borking your system.  I wouldn't worry too much about what was upgraded, unless you are just dying to know.  I would recommend looking at what is listed before pushing the button in the future.

/var/log/apt and /var/log/dpkg will contain your installation and upgrade history.

Yes, there will be follow-on updates, but if you update regularly that will all come out in the wash.

---

### Post by houndhen on 2012-09-04
Naw, I was talking about an upgrade and not an update. I have done the updates and the partial upgrade and all seems fine. My only concern was "partial upgrade" implies that more upgrade will be coming later. Just curious.

---

### Post by QIII on 2012-09-04
What I meant was that you don't appear to have been talking about a version upgrade (from, say 11.10 to 12.04), but a routine update/upgrade, which updates sources and then upgrades packages in your current Ubuntu version.  That is done periodically on line and does not require a new disk to be burned.

A partial upgrade can leave interrelated packages (dependencies, for instance) in a state that will cause problems.

---

### Post by este.el.paz on 2012-09-05
Question has been moved to new thread in DE: **Would fresh install of nv be erased with a kernel upgrade?**

e.e.p.

---

