---
title: "Graphics card"
date: 2011-04-13
forum: Desktop Environments
---

### Post by vicke4 on 2011-04-13
I'm new to Linux and Ubuntu 10.10.i installed Ubuntu 10.10 yesterday in my laptop.my laptop has ati hd radeon 4350 graphics card.where i can find a correct driver for that card in Ubuntu?please help me.

---

### Post by howefield on 2011-04-13
Have you tried System > Administration > Additional Drivers to check if it offers any drivers for your card ?

If you haven't updated your sources list since installing, I'd do that first.

Open a terminal (Applications > Accessories > Terminal) and type 

```
sudo apt-get update
```

---

### Post by 3Miro on 2011-04-13
> **vicke4 said:**
> I'm new to Linux and Ubuntu 10.10.i installed Ubuntu 10.10 yesterday in my laptop.my laptop has ati hd radeon 4350 graphics card.where i can find a correct driver for that card in Ubuntu?please help me.

Unlike windows, Ubuntu comes with a lot of very good default drivers. I have both Radeon 4250 and 4850, and for both of those, I recommend you stay with the default driver (i.e. don't do anything).

If you find that things are not working as you expected and/or you need some additional functionality, then you can try the additional drivers (System -> Admin -> Additional Drivers).

---

