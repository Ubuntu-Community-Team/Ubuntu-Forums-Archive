---
title: "Dual Screen Graphics Card"
date: 2012-08-01
forum: Desktop Environments
---

### Post by danielgroves on 2012-08-01
Hi,

My work machine currently runs Ubuntu 12.04 x64, and to maximise productivity I would like to add a new graphics card (PCI Express) that will allow me to support two (or more!) monitors. The card needs to be as cheap as possible and I currently have a pair of VGA screens to use with it. 

The card must support a low profile case, I do have a DVI to VGA adapter which I can use with it if need be. 

So what card(s) would you advise?

Dan.

---

### Post by 3Miro on 2012-08-01
What card are you using now? If you want to use the new card with the old one, you should get the same card or the same brand. Mixing different graphics cards is not impossible, but it is not a good idea.

For a desktop, I would go with some cheap Nvidia like GT210 or GTX430/520. I also have AMD 6850 at work and it works great with two monitors, 6850 is higher end card, but I am sure the cheaper ones will work fine (if you are getting AMD then make sure to pick one of the newer cards like 6xxx or 5xxx, 4xxx will probably work, but I wouldn't buy anything older). 

I think pretty much all modern Nvidia and ATI cards would support dual monitor.

---

### Post by danielgroves on 2012-08-01
Thanks for your response.  

I'm currently using the integrated card thats on the machines motherboard, so no need to worry about using one thats the same brand etc as this one will automatically disable itself in the if an external card is supplied. Are their any particular cards with known issues in Ubuntu?  It's been a while since I've had a Linux desktop environment, as I primarily work with it remotely via SSH.  

Thanks again.

---

### Post by 3Miro on 2012-08-01
> **danielgroves said:**
> Thanks for your response.  

I'm currently using the integrated card thats on the machines motherboard, so no need to worry about using one thats the same brand etc as this one will automatically disable itself in the if an external card is supplied. Are their any particular cards with known issues in Ubuntu?  It's been a while since I've had a Linux desktop environment, as I primarily work with it remotely via SSH.  

Thanks again.

Avoid old AMD/ATI cards and everything that has to do with hybrid graphics (i.e. Optimus). 

Ubuntu Unity (11.10 and newer) has higher requirements on the video card compared to older Ubuntu or other DE. I would recommend going with Nvidia GTX (i.e. don't use GeForce 9xxx or older). AMD 5xxx and newer should work well too (unless you want to play wine games, everything else works fine).

Actually any new video card would be fine for Unity, you should be worried only if you are getting an old used video card.

---

### Post by Ubun2to on 2012-08-01
Well, Unity doesn't require a super intensive graphics card, but you should still try to get one that was released after 2008. That should fulfill the requirements for Unity 3D.
I recommend buying a video card off Amazon-huge discounts in prices.

---

### Post by 3Miro on 2012-08-01
> **Ubun2to said:**
> Well, Unity doesn't require a super intensive graphics card, but you should still try to get one that was released after 2008. That should fulfill the requirements for Unity 3D.
I recommend buying a video card off Amazon-huge discounts in prices.

Ubun2to has a good point, I should clarify myself.

Unity 3D requires certain desktop effects. Video cards differ in speed and support for standards. For example, GTX280 is a faster video card than GTX430, however, the 430 version supports some effects that 280 doesn't have. Unity requires effects, not speed.

Any new video card would be good enough. If you are buying a used one, go for Nvidia GTX or GT series or AMD 5/6/7xxx series.

---

### Post by danielgroves on 2012-08-02
So one of these, for example, would be ok? [http://www.overclock.co.uk/product/Palit-1024MB-DDR3-GeForce-GT-520-DX11-HDMI-DVI--VGA--PCI-E-RetQail_41675.html](http://www.overclock.co.uk/product/Palit-1024MB-DDR3-GeForce-GT-520-DX11-HDMI-DVI--VGA--PCI-E-RetQail_41675.html)

Any issues anyone can foresee with one?  I should not I don't need anything amazing, as a web developer I jsut want to be able to spread out with some extra screen space, as a long as Ubuntu will run smoothly on it with a pair of screens that my only requirement.

---

### Post by 3Miro on 2012-08-02
> **danielgroves said:**
> So one of these, for example, would be ok? [http://www.overclock.co.uk/product/Palit-1024MB-DDR3-GeForce-GT-520-DX11-HDMI-DVI--VGA--PCI-E-RetQail_41675.html](http://www.overclock.co.uk/product/Palit-1024MB-DDR3-GeForce-GT-520-DX11-HDMI-DVI--VGA--PCI-E-RetQail_41675.html)

Any issues anyone can foresee with one?  I should not I don't need anything amazing, as a web developer I jsut want to be able to spread out with some extra screen space, as a long as Ubuntu will run smoothly on it with a pair of screens that my only requirement.

Should be fine.

---

### Post by danielgroves on 2012-08-02
> **3Miro said:**
> Should be fine.

Thanks, got one on order now so hopefully that'll be up and running early next week.

---

### Post by SteveHillier on 2012-08-03
> **danielgroves said:**
> as a long as Ubuntu will run smoothly on it with a pair of screens that my only requirement.

Daniel, I have been running two monitors on 12.04 without any problem

I am now trying to get two graphics cards working so that I can go up to 4 screens and I cannot seem to get both cards to work together, however....

The one issue I have is that most of my monitors are VGA only and so I have to try to use a DVI / VGA converter but...
the newer DVI sockets have a smaller long slot and no pins either side of them.  All of the adapters I have come across seem to have a longer slot and four pins.  They don't fit!!

---

### Post by danielgroves on 2012-08-03
Thanks for your help everyone.  The card just arrived, poped it in and it started working without any issues.  Chnaged it from mirroring mode into extended desktop and it performeing floorlessly.  

Thanks Again,

---

### Post by 3Miro on 2012-08-03
> **danielgroves said:**
> Thanks for your help everyone.  The card just arrived, poped it in and it started working without any issues.  Chnaged it from mirroring mode into extended desktop and it performeing floorlessly.  

Thanks Again,

Glad to hear that. If you have no more questions on this topic, could you please mark the thread as "Solved", it helps us keep the forum organized.

---

### Post by Ubun2to on 2012-08-03
> **danielgroves said:**
> **_Chnaged_** it from mirroring mode into extended desktop and it **_performeing_** **_floorlessly_**.

LOL! Anyway, it took me awhile to get my graphics card to support multiple monitors.

---

### Post by danielgroves on 2012-08-06
> **Ubun2to said:**
> LOL! 

My spelling and grammar are bad at the best of times, mix that with a mobile device, and, well you just saw how bad the result is.

---

