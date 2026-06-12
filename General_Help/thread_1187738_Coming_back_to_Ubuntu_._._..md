---
title: "Coming back to Ubuntu . . ."
date: 2009-06-15
forum: General Help
---

### Post by StarsAndBars14 on 2009-06-15
Played around with Vista for a while, been getting tired of it.  It freezes up on me twice every day, when I try to get on my wireless network, when iPod is attached to computer during boot, etc.  So I'm fixing to clean my laptop and just install Ubuntu 9.

Can I get any user feedback experience-wise?  Is it, in most day-to-day tasks, better than 7.10?

And who can tell me how Wine handles browser apps under this new version of Ubuntu?  I play online poker regularly and don't really want to lose that in the switch.  

Thanks.

---

### Post by 4Orbs on 2009-06-15
My wife plays online poker without using Wine. But Opera is the only browser on Ubuntu that works with the poker graphics. Don't know why.

---

### Post by loomsen on 2009-06-15
>  But Opera is the only browser 

signed

>  I play online poker 

Depends on the site you play at. Party Poker won't work, FullTilt will work with some borked graphics, but it's playable. Stars will work just fine through wine.

However, if you use to play at smaller cardrooms or have accounts anywhere, a VirtualBox will probably be what you want (or any other virtualization solution)

Especially if you use tracking progs like HoldemManager or Pokertracker.
What's nice, tho, you may setup a postgresql server on your linux machine and connect your virtualbox through the virtual subnetwork created.
I prefer the virualization over wine. Plus, I need the auto-hotkey scripts (betpot etc) which won't integrate very well through wine.

When I set mine up, I took a XP.iso and nlite to strip everything off I don't need. Made it ~300 MB from initial 680 or so.
If you need win only for online poker, I'd suggest looking into it.

---

### Post by TheNosh on 2009-06-15
> **StarsAndBars14 said:**
> Is it, in most day-to-day tasks, better than 7.10

well i finally got my own computer and installed ubuntu when 8.04 came out and i loved it, but i liked 8.10 even more, and now i like 9.04 better still. so never having used 7.10 i can't really speak from experience with that release, but things have gotten progressively better.

 i would also suggest using the EXT4 filesystem, it's fast as hell. some people have reported data loss though

also if you have intel graphics most people would advise that you go with 8.04 LTS or 8.10

---

### Post by rizman on 2009-06-15
> **TheNosh said:**
> 
also if you have intel graphics most people would advise that you go with 8.04 LTS or 8.10

Also, if you have an older ATI GPU and you want to play 3D intensive games (or for that matter any 3D application). Ubuntu 9.04 uses Xserver 1.6 which is only compatible with the catalyst 9.4 and higher drivers. Howere, ATI dropped support for a lot of cards in the catalyst 9.4 drivers. 2D works just fine in Jaunty however using the open-source ATI drivers.

---

### Post by wcutrombonekid on 2009-06-15
> **TheNosh said:**
> 
also if you have intel graphics most people would advise that you go with 8.04 LTS or 8.10

i think its only the intel X3000 and X3100 if i am correct.  Although there my be an ATI in there somewhere too

---

### Post by StarsAndBars14 on 2009-06-15
> **rizman said:**
> Also, if you have an older ATI GPU and you want to play 3D intensive games (or for that matter any 3D application). Ubuntu 9.04 uses Xserver 1.6 which is only compatible with the catalyst 9.4 and higher drivers. Howere, ATI dropped support for a lot of cards in the catalyst 9.4 drivers. 2D works just fine in Jaunty however using the open-source ATI drivers.

Card on my lappy is an ATI Radeon X1200.  Should work fine.

---

### Post by rizman on 2009-06-15
> **StarsAndBars14 said:**
> Card on my lappy is an ATI Radeon X1200.  Should work fine.

Sorry to disappoint you, but check this out:
[http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English&rev=9.3&ostype=Linux%20x86](http://support.amd.com/us/gpudownload/linux/legacy/Pages/radeon_linux.aspx?type=2.4.1&product=2.4.1.3.17&lang=English&rev=9.3&ostype=Linux%20x86)
The X1200 is listed as legacy support. 

I said that old cards have been moved to legacy support, but some people have cards less older than a year and they have also been put on legacy support. So 'old' is pretty relative in this context.

But as I said, if you don't need intensive 3D, than Jaunty is fine. It worked pretty well for me. But as I'm also a hobby game developer, I switched to Hardy this weekend because 3D wasn't good enough for my needs under Jaunty with the open-source drivers.

---

### Post by StarsAndBars14 on 2009-06-15
> **rizman said:**
>  
I said that old cards have been moved to legacy support, but some people have cards less older than a year and they have also been put on legacy support. So 'old' is pretty relative in this context.


Its less than two years old.  I don't really think there'll be many problems with it.  3D gaming works fine for me on Windows - but I don't do much of that anymore so . . . yeah.

---

### Post by ActiveFrost on 2009-06-15
> **4Orbs said:**
> My wife plays online poker without using Wine. But Opera is the only browser on Ubuntu that works with the poker graphics. Don't know why.

Betway poker works just fine ( at least it works for me :D ).

---

### Post by rizman on 2009-06-15
The final choice is up to you of course. Just wanted to point that out. The problem is that even though 3D works in Windows, it will not work in Jaunty. (Well, it will work, but not very good). The reason is, as I said, that XServer 1.6 does not support the catalyst drivers before version 9.4. Your card, among others, has been put on legacy support as of cataylst drivers 9.4. That means that you will, under Jaunty, not be able to use ANY version of the proprietary ATI drivers. You will be bound to using the open-source ati/radeon drivers. They work very good with 2D, and have some basic 3D support, but it is far from being as good as the ATI drivers.

---

### Post by 3startuna on 2009-06-15
Time to play some ACDC - Back in Black 

:D

---

