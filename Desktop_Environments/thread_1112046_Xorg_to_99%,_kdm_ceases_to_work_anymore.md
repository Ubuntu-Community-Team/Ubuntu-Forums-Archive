---
title: "Xorg to 99%, kdm ceases to work anymore"
date: 2009-03-31
forum: Desktop Environments
---

### Post by ryanswan on 2009-03-31
I have a new system at home that I've loaded a few times with Kubuntu 8.04 and I keep running into this same problem.

I leave my computer on for an extended period of time, I come back to it, the windowing environment is basically frozen but I'm still able to ssh to the box.  I ssh in, run TOP and see Xorg taking 99% of the CPU, so I kill it and restart kdm and then kdm runs but refuses to be visible.  The only solution thus far is to reload, which gives me 1-2 days before lockup again.

Also, now I'm forced to load my machine with the OEM option enabled and then apt-get update and apt-get upgrade before I can see a windowing environment.

My first instinct is video, I'm using an Nvidia 9600 GT 512mb rev a1.

Any advice for this problem or how to start deciphering it?

Thanks.

---

