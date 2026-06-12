---
title: "Ubuntu boot from snapshot"
date: 2008-12-31
forum: General Help
---

### Post by jreberry on 2008-12-31
First, some background info. I was a Windows user since the 66Mhz days. I'm very comfortable in Windows and I'm the guy family and friends are constantly asking for help. About a year ago I made the jump to Ubuntu not knowing what to expect. I've been EXTREAMLY happy with the jump. Even my wife likes it better. However, the problem is that I had to start learning all over again. After a year  I would consider myself an advanced beginner, so please keep the solutions around this level if possible.  :-)

Now for the question; is there a way to make Ubuntu load from a snapshot every time it boots? I'd like to do this because generally we are simply using the computer, not adding stuff to it. It would be nice to load from an image each time so that the wife/kid/myself can't accidentally mess anything up. Under normal conditions, we would simply load and use the saved snapshot. Ideally, there would be some sort of "save" button within Ubuntu that I could click to save a new snapshot if I just installed/updated something.

I currently use this setup in both VMware and VirtualBox so the XP client loads exactly the same each time. If I need to install or modify something I simply take a new snapshot. I've become addicted to the ability to play with things with no worry of the consequences. I'd love to have that same ability with the main Ubuntu operating system as well.

I'm guessing the answer is there is no simple solution, but I thought I would ask just in case.

For what it is worth, the machine is an oldish Dell 6000 laptop, 1.5 Gig Ram, 1.6 GHz Processor. I'm using full disk encryption, all software is up to date.

Thanks in advance, this is my first post, but these forums have been a HUGE help over the past year.

--Jon

---

### Post by dcstar on 2008-12-31
> **jreberry said:**
> 
.........
Now for the question; is there a way to make Ubuntu load from a snapshot every time it boots? I'd like to do this because generally we are simply using the computer, not adding stuff to it. It would be nice to load from an image each time so that the wife/kid/myself can't accidentally mess anything up.
........

If you don't want people to have the ability to "mess anything up" then just create user accounts without Administrator privileges and then you can be sure that someone logging in with those cannot affect the underlying system.

That is how proper multi-user systems are suppose to work, the default Ubuntu user only has Admin privileges because **someone** has to.

Make an Admin account for the occasional time that you need to do anything along those lines, but don't use it for anything else and you will have a rock-solid system that will be stable and useful for a very long time.

---

### Post by jreberry on 2009-01-02
Thanks for the info dcstar, 

That is the setup I used for a few years with XP. The limited user accounts had some annoying quirks, but there were workarounds for most of them. Eventually I ended up going back to one admin account because it was more end-user friendly. I currently make a full disc image every month to fall back on when (not if) something goes crazy.

I may give multiple user accounts a try with Ubuntu as you suggested. I had thought auto loading from a snapshot would be more fail proof and end-user friendly (depending on load time).

Thanks for the suggestion,
--Jon

---

