---
title: "cedega - opengl and 3d acceleration failed"
date: 2006-06-30
forum: Gaming &amp; Leisure
---

### Post by disturbd on 2006-06-30
I installed Cedega yesterday but opengl and 3d acceleration fail when i try to check them. I'm pretty new to linux so im don't know where to start. Thanks.

---

### Post by _simon_ on 2006-06-30
i'm guessing it's your video driver.

What graphics card do you have and what driver does it say is being used in Xorg?

To check do this from terminal: ```
gedit /etc/X11/xorg.conf
```

and copy the bit about your graphics, e.g. for me it's:

Section "Device"
    Identifier     "NVIDIA Corporation NV40 [GeForce 6800]"
    Driver         "nvidia"
    Option	   "NoLogo"
EndSection

---

### Post by disturbd on 2006-06-30
when i do that command in terminal the file it opens is blank

but the video card in my laptop is ATI MOBILITY RADEON 9550

---

### Post by Tomosaur on 2006-06-30
it's /etc/X11/xorg.conf

no capitalisation of xorg.conf

---

### Post by _simon_ on 2006-06-30
sorry! - my bad and now corrected :oops:

---

### Post by disturbd on 2006-06-30
Section "Device"
	Identifier	"ATI Technologies, Inc. RV350 NP [Mobility Radeon 9600/9700 M10/M11]"
	Driver		"ati"
	BusID		"PCI:1:0:0"
EndSection

thats right. but in cedega configuration it says my video card is a Mesa project

---

### Post by disturbd on 2006-06-30
i tried changing it to the ati stuff but it didn't work

---

### Post by _simon_ on 2006-07-01
may I suggest you post on the ATI forum at Transgaming? :)

[http://transgaming.org/forum/viewforum.php?f=43&sid=3b59c1340a266ad17894f89a99c23657](http://transgaming.org/forum/viewforum.php?f=43&sid=3b59c1340a266ad17894f89a99c23657)

---

### Post by deathbyswiftwind on 2006-07-01
All you need to do is install your ati driver correctly and make sure your xorg xonfig is set to use the fglrx driver. Mine does the same exact thing when its not setup correctly

---

### Post by sethmahoney on 2006-07-01
The first step I'd recommend is following the directions on this page:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

