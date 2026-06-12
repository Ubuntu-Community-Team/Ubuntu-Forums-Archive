---
title: "Source games with Cedega black screen"
date: 2007-08-27
forum: Gaming &amp; Leisure
---

### Post by Hyter on 2007-08-27
I have Cedega 6.0.2 and Ubuntu 7.04

I have successfully installed Steam and all of my source games, but I am unable to play them. Whenever I start a source game the screen just goes black.

I've searched around, but didn't find many answers. One possible answer was it was because of my ATI Radeon x800 graphics card.

Does anyone else have more information?

---

### Post by justiN_ on 2007-08-30
i have the same problem.
-same versions
-same games
-same video card (x800GTO)

help?

---

### Post by Hyperkill on 2007-08-30
You should try loading it up using wine and see if that works for you.  I've been able to get a really smooth running version of CS:S using it.

---

### Post by alican timur on 2007-08-30
how do i install steam with wine? the steam setup file is an .msi file and it says bad exe extension in console when i try to run it.

---

### Post by splintercellguy on 2007-08-30
wine start TheMsiFile.msi

---

### Post by Hyter on 2007-09-01
I tried it with Wine, but I am still having problems.

First it tells me that my video driver is out of date, but I tell it to continue anyway.
It resizes my screen, and I can see the CS:S loading screen, but then it goes back to my desktop.

---

### Post by shadycuz on 2007-09-02
Im using wine, I have a ati aiw x800xl using the priotory drivers or not I still get a black screen, and i can hear the sound of my mouse moving over the buttons. Any one know how to resolve this? I would love to play my game.

---

### Post by jacob01 on 2007-09-02
> **splintercellguy said:**
> wine start TheMsiFile.msi

to run the msi  navigate to were it is stored and then run

```
wine msiexec /i SteamInstall.msi
```

---

### Post by chadlongstaff on 2007-09-15
I'm having the same problems with the same software but an nVidia 8500 GT. When games in Steam get anywhere they just do a little resolution switching then crash. Tried disabling composite, had no effect, otherwise my googling is hitting a brick wall.

---

