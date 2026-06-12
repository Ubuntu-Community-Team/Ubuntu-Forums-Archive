---
title: "Install on multiple computers with same settings+apps"
date: 2009-03-07
forum: General Help
---

### Post by abyrne on 2009-03-07
Hi,

I'm trying to install Ubuntu on about 50 different computers and I want all those computers to have the same configuration (users, apps, settings, ect.). I don't want to go to every computer and put in the settings by hand. Is there any way to automatically get the same config on every computer I install Ubuntu onto?

Go easy on me, I'm very new at this.

Thanks!

---

### Post by hexanol on 2009-03-07
Well, there's partimage, if every machine has the same (or really close) hardware. You install Ubuntu on only one machine, then you create an image of the installation, then you only need to restore the image on every machine.

There's also clonezilla that is even more powerful, but more complex.

---

### Post by abyrne on 2009-03-07
I was thinking about that but only about 7 of those 50 computers are the same. All the other ones are all refurbs.

---

### Post by abyrne on 2009-03-07
Bump

---

### Post by abyrne on 2009-03-09
What? No one knows how to do this?:(

---

### Post by davidryder on 2009-03-09
If they don't all have the same hardware it's not possible, or you have to create an image for each computer that has different hardware. You can try to create one and restore them but chances are if the hardware is even slightly different the system won't even boot.

At least, that is my experience with imaging.

---

