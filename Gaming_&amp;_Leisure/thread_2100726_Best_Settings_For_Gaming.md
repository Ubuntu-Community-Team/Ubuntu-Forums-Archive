---
title: "Best Settings For Gaming"
date: 2013-01-02
forum: Gaming &amp; Leisure
---

### Post by bman on 2013-01-02
I have Ubuntu 12.04 installed.

I have a ATI Radeon HD 5850 graphics card, currently running the default Ubuntu drivers.

I want to test out Steam and play a game or to and they are telling me to update drivers.

Every time I have tried the ATI/AMD drivers I have had issues.

For my system, what is the best option to use?

There are 2 options in additional drivers, and I believe 2 versions on the AMD website.

Suggestions?

---

### Post by mentorious on 2013-01-02
I've ATI 5000HD and [those drivers]("http://www2.ati.com/drivers/beta/amd-driver-installer-catalyst-12.11-beta11-x86.x86_64.zip") installed (12.11beta11 for graphic cards newer than HD5000). 

Everything (Steam, Team Fortress 2, Serious Sam, Left4Dead2 etc.) works fine :)

But it's little issue, after kernel update you must reinstall the drivers. otherwise x-server doesn't run when system starting up.

---

### Post by bman on 2013-01-02
Yea I tried running Team Fortress 2 on the default drivers and just get an error message.

I will try those drivers, just the last time I updated drivers I couldn't get back into Ubuntu after a reboot lol

Side question, how did you install Left4Dead2? I have that game in Steam, but it does not show up on the list of Linux games?

---

### Post by Darksthour on 2013-01-02
That's because only a select few games are available for linux at the moment. Maybe when it leaves beta all games will become available.

---

### Post by bman on 2013-01-02
> **Darksthour said:**
> That's because only a select few games are available for linux at the moment. Maybe when it leaves beta all games will become available.

UH ok? He said he had Left4Dead2 working, its not on the linux list, that is why I asked? What does that have to do with the beta.

---

### Post by mentorious on 2013-01-02
> **bman said:**
> UH ok? He said he had Left4Dead2 working, its not on the linux list, that is why I asked? What does that have to do with the beta.

It's a little bit complicated. I joined to the closed beta testing in October, then I had L4D2 and I played on those drivers. Members in beta can playing a few games but in December beta has been expired and I lost access to games. That's all. I don't know what's the matter with L4D2 now, maybe they're testing "privately".

> Yea I tried running Team Fortress 2 on the default drivers and just get an error message.

When I had default driver in Ubuntu I had also errors. I remember that was something with rgb and Opengl.

Anyway, before install from run file make sure, whether old fglrx drivers are deleted (sudo apt-get remove --purge fglrx* etc..)

---

### Post by bman on 2013-01-02
So I should do that command even if I have never installed any ATI drivers before?

---

### Post by mentorious on 2013-01-02
> **bman said:**
> So I should do that command even if I have never installed any ATI drivers before?

Nope, now go to install ;)  

I meant only when have you **fglrx** drivers installed early.

---

### Post by bman on 2013-01-02
Alright good to know, thanks.

---

### Post by bman on 2013-01-04
I installed the latest drivers (12.11) and things almost seem worse now.

Opening and closing my browser seems more choppy then before. Shouldn't it be better?

---

