---
title: "Weird refresh rate options don't jive w/reality"
date: 2007-06-06
forum: Desktop Environments
---

### Post by timzak on 2007-06-06
Just a question out of curiosity:

When going to the resolution/refresh rate changer, does anyone else have weird refresh rate options like 50Hz, 51Hz, etc, that don't match up with the actual refresh rate?

This is in a fresh install of Fiesty, with restricted drivers enabled.  When restricted drivers are disabled, the refresh rates shown are accurate.  I've seen this on two machines, both with nvidia cards.  One machine has a Gefore3 Ti200 AGP and the other has a Geforce 6800GS AGP.

This is only in System->Administration->Screen Resolution.  If I look in xorg.conf everything there is correct.

Just seems like a little bug to me.

---

### Post by meng on 2007-06-06
Yes, I have this. Feisty says it is refreshing at 50 Hz, my Samsung 204B says 60 Hz. I did not experience this with Dapper.

---

### Post by Nythain on 2007-06-06
its a weird issue with edgy and feisty and the nvidia drivers... so i set my resolution with gksudo nvidia-settings instead of the default way of doing it

---

