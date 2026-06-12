---
title: "Why/how do I have desktop effects without installing FGLRX? (Lucid Daily)"
date: 2010-04-24
forum: Desktop Environments
---

### Post by sparrowkc on 2010-04-24
I have a Dell Studio 1537 Laptop with what lspci calls an "ATI Technologies Inc Mobility Radeon HD 3400" graphics card. Today I downloaded a daily image of Lucid, threw it on a USB drive, and booted it up.  As I go to install the restricted driver for my graphics card, I notice that clicking on a panel item triggers the star burst effect.  Come to find out that I can set desktop effects to "extra" and get smooth wobbly windows and everything.

Why are desktop effects working?  I've always had to install FGLRX before, did the open source driver somehow get 3D support?  Am I missing something?  I almost feel like Compiz is performing better-- smoother, less tearing, etc.

---

### Post by 3Miro on 2010-04-24
> **sparrowkc said:**
> I have a Dell Studio 1537 Laptop with what lspci calls an "ATI Technologies Inc Mobility Radeon HD 3400" graphics card. Today I downloaded a daily image of Lucid, threw it on a USB drive, and booted it up.  As I go to install the restricted driver for my graphics card, I notice that clicking on a panel item triggers the star burst effect.  Come to find out that I can set desktop effects to "extra" and get smooth wobbly windows and everything.

Why are desktop effects working?  I've always had to install FGLRX before, did the open source driver somehow get 3D support?  Am I missing something?  I almost feel like Compiz is performing better-- smoother, less tearing, etc.

The open source driver does support 3D, just not very well. Besides many effects don't need that much of power, I can do the desktop wall slide from a Live CD on all three types (Intel, ATI, NVIDIA).

---

### Post by clhsharky on 2010-04-24
HI sparrowkc

The OSS drivers does have some advantages over fglrx, some you have named others are
Better 2D acceleration, more stability, and you can use a newer Kernels with more features and-or stability.
Example latest .34 kernel has power management to help laptops.

Sharky

---

### Post by pazuzuthewise on 2010-05-01
Indeed, I also have a radeon 3470 and have observed much better 2d acceleration with the open source driver than with fglrx, and similarly good 3d (at least in X, haven't tried video playback, nor games.)

The only problems with the open source driver where: no bootsplash - that is not so bad since it boots fast - but also it didn't power off. When shutting down, I got to the same weird looking screen as during boot, and there it stayed. I had to press the power button to halt it.

On the other hand, with fglrx I get to see the wonderful bootsplash (I still don't get it why the old one wasn't good enough, it wasn't as fast as this, but it was stable, what cannot be said about plymouth - and this is supposed to be a stable LTS version), and, more importantly, it shuts down / restarts OK.

But there seems to be a regression in respect to the 2d acceleration of fglrx. In Karmic it wasn't something to write home about, but it worked. Here, in Lucid, when moving windows around, it's ugly (leaving trailing marks) and extremely slow - like as if I was running it on a pentium mmx, not a dual-core system - and eating up to around 80% CPU.

And I don't want compiz, and more so since with it activated, I cannot drag a window to another workspace using workspace-switcher.

Sorry Ubuntu Lucid, you're beautiful, but this just means you're not even near to the quality, stability and user-friendliness that Canonical uses to describe you.

---

### Post by screaminj3sus on 2010-05-01
For a laptop you may want to isntall fglrx anyway, the oss drivers have NO power management, my laptop is like its filled with magma when I use them. i find besides that they are all around better than fglrx though. Compiz with No tearing, video with no tearing. fglrx still sucks balls in those areas.

And @ the post above I get the bootsplash with the oss driver... the nice high res plymouth one too. Fglrx gets the *** ugly low res one because it doesnt support kms. And yeah I agree the tearing in fglrx moving windows sucks. it does it playing videos too :/

---

### Post by screaminj3sus on 2010-05-01
> **clhsharky said:**
> HI sparrowkc

The OSS drivers does have some advantages over fglrx, some you have named others are
Better 2D acceleration, more stability, and you can use a newer Kernels with more features and-or stability.
Example latest .34 kernel has power management to help laptops.

Sharky

Wait you say the oss deriver in that kernal has power management? PLEASE TELL ME HOW TO USE THE OSS DRIVER WITH POWER MANAGEMENT AND I WILL LOVE YOU FOREVER.

The oss driver is so much betetr than fglrx but my laptop gpu gets 60+ degrees Celsius just idling.

EDIT: So I updated my kernel to 2.6.34 and updated my oss drivers via xorg edgers, I think there may be some power management now, but its hard to tell cause my laptop is already really hot due to being on my bed and its really damn hot out, I'll test more tomarrow but the fan is not blasting like it was and it seems cooler :)

---

