---
title: "AWN grouping all my wine applications under one icon"
date: 2010-05-14
forum: Desktop Environments
---

### Post by eddyojb on 2010-05-14
Hi,

I'm having an issue with my AWN dock where I have enabled it to  'group similar applications', i.e multiple windows of the the same application

In 9.10, AWN distinguished between different WINE applications and used their native icons.

In 10.04 AWN doesn't distinguish, see the pic below

[ATTACH]156931[/ATTACH]

As you can see AWN groups my WINE applications under one icon, the spotify icon and you can see the MS Word logo to the right. This is very irritating since I would like to have separate WINE shortcuts on my taskbar! I'm sure this will affect some other users too.

Anyone know how to sort this out?

N.B I can't use cairodock as I have issues with freezing and icons not appearing, and i feel docky isn't up to speed with the same functionality as the others for the time being.

---

### Post by brucemartin on 2010-05-14
this has been fixed in the latest AWN unstable available via AWN testing PPA: 

sudo add-apt-repository ppa:awn-testing

---

### Post by eddyojb on 2010-05-15
Many thanks. I've added this to my repository but can't see any updates when using sudo-update or through the update manager. I take it the update isn't available yet so I'll keep my eyes peeled

---

### Post by nosfur on 2010-07-08
Well I just went to awn preferences then advanced tab and in there found matching strength and typed in 25. And it did solve mine problem.

---

### Post by undrline on 2013-05-01
> **nosfur said:**
> Well I just went to awn preferences then advanced tab and in there found matching strength and typed in 25. And it did solve mine problem.
Whoohoo!  Thank you.

---

### Post by oldos2er on 2013-05-01
Closed.

---

