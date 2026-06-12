---
title: "[SOLVED] AWN Help"
date: 2007-09-02
forum: Desktop Effects &amp; Customization
---

### Post by BadPenguin86 on 2007-09-02
Not to beat a dead horse about avant window navigator.. but I have got mine to work fairly well, but it is not at the bottom of the screen, nor centered, and I don't know how to fix it. Anyone know how? I have tried completely removing it and installing it again... but no dice. Any help is appreciated.

---

### Post by hyperair on 2007-09-02
Well where is it then? You could try removing your AWN configuration. 
```

rm -r ~/.gconf/apps/avant-window-navigator

```

Then restart.

---

### Post by Bob_Mendon on 2007-09-02
I'm running dualview and had to play with different resolution and desktop settings until I got it right. Also restart X after each change and make sure tou have your compiz, beryl or emeral running each time. I'm not by anymeans an advanced user, so I just try different thinks until I get something working.

---

### Post by BadPenguin86 on 2007-09-02
It is right above where the bottom panel would be and cenetered like it should be for a 4:3 resolution monitor, instead of widesreen

---

### Post by BadPenguin86 on 2007-09-02
Sorry guys, I went into the configuration editor and found that there is a way to force it to a resolution, that fixed it, it defaulted to 1024x768 and I have 1280x800. It is working perfectly now. Thanks for the help though.

---

