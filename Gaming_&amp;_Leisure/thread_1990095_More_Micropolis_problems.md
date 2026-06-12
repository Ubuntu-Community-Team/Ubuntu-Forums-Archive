---
title: "More Micropolis problems"
date: 2012-05-29
forum: Gaming &amp; Leisure
---

### Post by Erik1984 on 2012-05-29
I posted yesterday about the inability to change the save game folder but that was just a minor issue. The game seems unstable and crashes quite often. The behavior seems to be related with popup windows the game opens (i.e. for displaying the budget or the built in file browser).  I started the  game from the terminal to catch error messages. Everytime the game starts it reports:

```

Adding a player on :0 ...
Darn, X display ":0" claims to support the shared memory extension,
but is too lame to support shared memory pixmaps, so Micropolis will run slower.
Please complain to your X server vendor, The X.Org Foundation

```Could this have something to do with Kwin? I turned off all desktop effects to see if that made a difference but it still crashed and displayed the above warning. The actual crash causes the following report:

```
X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  40 (X_TranslateCoords)
  Resource id in failed request:  0x1a04795
  Serial number of failed request:  6507
  Current serial number in output stream:  6507
```Another session had the resulted in the same error with different numbers:

```

X Error of failed request:  BadWindow (invalid Window parameter)
  Major opcode of failed request:  40 (X_TranslateCoords)
  Resource id in failed request:  0x1a0529b
  Serial number of failed request:  477506
  Current serial number in output stream:  477506

```
Does anyone of you experience similar errors? I played Micropolis before on a previous version of Ubuntu (note I have Kubuntu now) and don't recall such crashes. Possible way to reproduce crash: set game speed to fast and click "continue" each time the annual budget windows appears.

And where could I report these errors? There is a Google code page for Micropolis but it doesn't seem very active (last version of the game released in 2008.

---

### Post by Erik1984 on 2012-06-04
*bump*

---

### Post by Erik1984 on 2012-06-11
*final bump*

---

### Post by Perfect Storm on 2012-06-11
Have you tried with another WM instead of kwin to confirm it? If so you better bug report it to the KDE folks.

---

### Post by Erik1984 on 2012-06-12
Thank you for responding. No, haven't checked another WM yet. For now I will let this rest and try Micropolis again when I upgrade to 12.04 (I'm still on 11.10) with Unity. If it works better in another WM I will file a bug @ bugs.kde

---

