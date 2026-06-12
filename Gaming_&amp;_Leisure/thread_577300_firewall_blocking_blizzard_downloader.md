---
title: "firewall blocking blizzard downloader"
date: 2007-10-16
forum: Gaming &amp; Leisure
---

### Post by steven182 on 2007-10-16
first off,

hello =] im new to the whole linux thing, ive got ubuntu 7.04 and beryl going looks fantastic. copied my entire programme files folder from my network into my wine C:\ so that it is in the same place as my other wine apps.

this seemed to work fine it opens up and runs allows me to log in but obviously blizzard being the arses they are, they decided to release a minor patch.

now then wow closes and up pops the oh so not fun blizzard downloader which insists i am behind a firewall, now to the best of my knowledge i dont have a firewall installed.

so basically how do i allow these ports that blizzard recomend you set your firewall to open through linux?

that would be a great help =]

i guess i could always download them on my xp pc but that would just be silly =p


Thanks all =]

---

### Post by TidusBlade on 2007-10-16
You can always download it from another site, check [this](http://www.wowwiki.com/Patch_mirrors) out.
Blizzard Downloader worked perfectly for me, so maybe it'd another computer...

---

### Post by steven182 on 2007-10-16
hmm was talking to someone i know who uses linux and they said that it shouldnt be blocked and should just download so god knows what ive done 

/shrug


thanks for the mirror site, never knew about them =]

---

### Post by derekr44 on 2007-10-16
The Blizzard downloader usually works, but it's not 100%.  Even for me, I had problems with it in Windows sometimes.

Downloading from a mirror is always the best IMO because the traffic is usually lighter anyway.

---

### Post by vacolten on 2007-10-16
If you're behind a router you need to open port forwarding on the following ports:

3724 TCP 
6112 TCP 
6881-6999 TCP 

The first two are necessary (so they say) for patching, the last range is mainly if you have more than one machine on your network playing WoW.

Also as an aside - make sure you chmod 777 Config.wtf.  I had everything working fine but it wouldnt bring me into the character screen until I made it global read/writable.

---

