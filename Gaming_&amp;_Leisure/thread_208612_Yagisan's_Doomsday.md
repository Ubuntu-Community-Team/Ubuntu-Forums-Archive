---
title: "Yagisan's Doomsday"
date: 2006-07-03
forum: Gaming &amp; Leisure
---

### Post by dalee on 2006-07-03
Hi,

Does anyone know if Yagisan is going to rebuild his superb Doom packages for Dapper? It's the one game I've really become addicted to.

I've got it running on an older box running Breezy and it's just awesome! Please Yagisan, I know your busy, but your Doom packages are the best!!!!

Thanks,
dalee

---

### Post by HAARP on 2006-07-04
Add to sources.list:

deb [http://users.lichtsnel.nl/~yagisan/ubuntu](http://users.lichtsnel.nl/~yagisan/ubuntu) dapper main restricted universe multiverse
deb-src [http://users.lichtsnel.nl/~yagisan/ubuntu](http://users.lichtsnel.nl/~yagisan/ubuntu) dapper main restricted universe multiverse

It will get you some errors when updating, but you can install the packages.
Still has some glitches, but works.
For example, Timidity, which plays the music, sometimes refuses to exit, which causes Doomsday to wait for the music to end before continuing (unless you do a killall -9)

---

### Post by dalee on 2006-07-04
Hi,

Thanks VERY much!

dalee

---

### Post by Yagisan on 2006-07-04
[QUOTE=dalee]Hi,

Does anyone know if Yagisan is going to rebuild his superb Doom packages for Dapper? It's the one game I've really become addicted to.

I've got it running on an older box running Breezy and it's just awesome! Please Yagisan, I know your busy, but your Doom packages are the best!!!!

Thanks,
dalee[/QUOTE]
Yes I am. I see that others have noticed my dapper works in progress. It's not finished yet, as real life, and my actually coding work on the Doomsday engine is taking uo a lot of my free time (Yes I'm a developer too now, not just the packager).

As mentioned by HAARP there are some issues with dapper, which is part of the reason I have not yet said, "hey all, I've got dapper packages now!"

---

### Post by HAARP on 2006-07-04
Hope you don't mind I let the cat out of the bag ;)

---

### Post by Yagisan on 2006-07-04
[QUOTE=HAARP]Hope you don't mind I let the cat out of the bag ;)[/QUOTE]
Not at all, as long as people realise that until my webpage says dapper (or edgy) is the current version, the packages are experimental and should be treated as such.

---

