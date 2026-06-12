---
title: "Cair Dock hidden behind window"
date: 2010-07-31
forum: Desktop Environments
---

### Post by Lenny212 on 2010-07-31
Hi, Cairo dock works sometimes and not others. It behaves as expected in every way (nearly) except it regularly appears under windows instead of on top making it impossible to use.

---

### Post by Mr_VeRiTy on 2010-07-31
Are you using the stable, or non-stable release? if non-stable I suggest you use the "reserve screen" view as it keeps windows from entering the space occupied by the dock, If your using the stable version, move your mouse to the bottom corners of the screen, the dock should reappear (unless its not on the bottom, in which case it will be another corner)

---

### Post by Lenny212 on 2010-07-31
Hi Mr_VeRiTy,
I am using the version in Synaptic Package Manager so assume it is the stable release. Nothing happens when I move mouse to corner of window. When I move mouse to the bottom of the window the Cairo Dock is activated (appears) but under the window. I know this because I have had semi-transparent windows open and I can see it underneath. It behaves normally apart from the fact it is buried underneath any open window.

---

### Post by hansdown on 2010-07-31
Hi Lenny212.

If you right click the dock, then click cairo-dock> configure> visibility of the main dock, you can set it to,

```
prevent windows from overlapping
```

---

### Post by Lenny212 on 2010-08-01
Thanks Hansdown but that doesn't solve the problem. When I first installed cairo dock it appeared above the window when the mouse was moved to the bottom of the screen and then disappeared off the bottom of the screen when the mouse moved away from it. This is a basic cairo dock functionality that isn't working.

---

### Post by Lenny212 on 2010-08-01
I think I have solved it. It is now working. I entered the Advanced Mode of configuration, clicked on System and unticked *Emulate composition with fake transparency?* I will continue to use it until I am sure it will stay fixed. Cairo Dock seems very temperamental.

---

### Post by hansdown on 2010-08-01
Nice work, Lenny212.

Hope you fixed it.

---

### Post by fabounet on 2010-08-02
this option ("Emulate composition with fake transparency") does make the dock stay under windows (on purpose).
you should not use it if you use Compiz, because it emulates composite, and Compiz already provides composite.

---

