---
title: "how do I change my color depth?"
date: 2009-06-12
forum: General Help
---

### Post by letmekilluplz on 2009-06-12
I want to play some games but the FPS is way to low how can I change the color depth to 16 bit?

---

### Post by unutbu on 2009-06-12
Edit your /etc/X11/xorg.conf. Change

```

Section "Screen"
	Identifier	"Default Screen"
EndSection
```

to

```

Section "Screen"
	Identifier	"Default Screen"
	DefaultDepth	16
EndSection

```
Then restart the X server by logging out and logging back in.

---

### Post by letmekilluplz on 2009-06-12
Well that worked but my FPS is still way to low to play anything... even though my computer surpasses all the recommended specs :(

---

### Post by unutbu on 2009-06-12
If you have an ATI or Nvidia card, do you have the restricted driver enabled?

---

### Post by letmekilluplz on 2009-06-13
I believe so but is there any way to check for sure?

---

### Post by unutbu on 2009-06-13
Click System>Admin>Hardware Drivers.
You should see a green ball next to the graphics driver you are using.

---

### Post by letmekilluplz on 2009-06-13
Yea all thats there is a wireless driver and I have an ATI Radeon Graphics. :o

---

### Post by letmekilluplz on 2009-06-13
Uh oh, the only driver for linux and my graphics card is for X 7.4 at the latest.

---

