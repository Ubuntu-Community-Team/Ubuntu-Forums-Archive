---
title: "Cant get Logitech F310 to work in Supertuxkart"
date: 2018-12-23
forum: Gaming &amp; Leisure
---

### Post by gh0zt362 on 2018-12-23
I ran jstest and checked button and stick configuration and operation and eveything is fine .  But when I start supertuxkart is doesnt respond at all to the game pad . 

Ubuntu Studio 18.10   Any ideas what I can try to get STK to see my joystick ?

---

### Post by deadflowr on 2018-12-25
There's a snap version so might be that one.
Try adding the ability to use joysticks via the snap connect command like so
```
sudo snap connect supertuxkart:joystick
```

---

### Post by gh0zt362 on 2018-12-31
Hey thanks , I'll try it out and let you know .

---

### Post by gh0zt362 on 2019-04-24
> **deadflowr said:**
> There's a snap version so might be that one.
Try adding the ability to use joysticks via the snap connect command like so
```
sudo snap connect supertuxkart:joystick
```

That actually worked . Yay Tux kart !   What is a " snap version " anyways ?

---

### Post by thenailedone on 2019-04-25
> **gh0zt362 said:**
> That actually worked . Yay Tux kart !   What is a " snap version " anyways ?

Snaps are a new way of packaging applications for Linux. Kind of a container with everything needed to run the application (starts to remove the headache of not having the right drivers in different distro's or even different versions of the same distro).

[https://snapcraft.io/]("https://snapcraft.io/")

Similar ideas are also available like [Flatpak]("https://flathub.org/home") which also works in Ubuntu

---

