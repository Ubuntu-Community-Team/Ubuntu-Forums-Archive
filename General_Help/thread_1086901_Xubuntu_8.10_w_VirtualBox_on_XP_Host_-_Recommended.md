---
title: "Xubuntu 8.10 w/ VirtualBox on XP Host - Recommended Memory Settings"
date: 2009-03-04
forum: General Help
---

### Post by malura on 2009-03-04
I'm planning on installing Xubuntu via VirtualBox on an XP host, and I was wondering how much memory (base and video) I should dedicate to Xubuntu for optimum performance. Also, should I enable 3D acceleration?

---

### Post by Het Irv on 2009-03-04
I don't know if you will need 3D, you might be able to get away without it, 512 base memory and 128 for video.  That should get you running reasonably smooth.

Running an OS natively will always give you better results, but Xubuntu is so light you shouldn't have many problems running it in VBox.

---

### Post by malura on 2009-03-04
Thanks a bunch! I've actually got it installed, and everything seems to be working alright. Question - is the lag associated with Flash games a result of the emulation? I've installed Feisty, Ibex, and Gutsy (through Virtualbox), and it seems like the lag is equally bad across all three.

---

### Post by Het Irv on 2009-03-04
Probably, since the keystrokes have to be interpreted by both the Host OS and VirtualBox.  Also keep in mind that VirtualBox doesn't emulate your hardware, it just emulates generic hardware, and interfaces with your own.  This means that the Guest OS can work just fine in the VBox, and not work natively.  *buntu is pretty good about working OOTB, but I just want to give you fair warning.

---

