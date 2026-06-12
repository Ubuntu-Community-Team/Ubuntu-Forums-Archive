---
title: "A Resolution Problem!"
date: 2009-03-17
forum: General Help
---

### Post by LazyLlama on 2009-03-17
I'm feeling like a bit of a muppet right now. I plugging in my Eee pc (with ubuntu) into my Monitor and changed the resolution correctly. Now, I didn't have a clue what the resolution was of my Eee so I set it randomly. And now,this resolution won't let me change the resolution, because the "Apply" button is off screen! I can't drag the window higher than the screen and I've tried plugging it back into my monitor but it doesn't stretch accordingly! I can't think of a possible way to apply the correct resolution! The enter button, as many times I've tried, doesn't work either...

Any help will be appreciated! I can't stand this resolution any more!

---

### Post by LegendofTom on 2009-03-17
You probably need to edit some config files, but try
```
dpkg-reconfigure xserver-xorg
```

---

### Post by LazyLlama on 2009-03-17
Thanks for your help, but, I didnt get anything about screen resolution there, just keyboard stuff - did I do somthing wrong?

---

### Post by lewmnik on 2009-03-17
press alt and drag the config window so that you can click the button (keep pressing the alt;))

---

### Post by ajgreeny on 2009-03-17
> **LegendofTom said:**
> You probably need to edit some config files, but try
```
dpkg-reconfigure xserver-xorg
```
On the assumption that the eeepc version of ubuntu is based on a standard 8.10, this command does not work any more and has not done so since hardy, IIRC.  lewmnik's answer should work best for you, I think.

---

### Post by LazyLlama on 2009-03-18
> **lewmnik said:**
> press alt and drag the config window so that you can click the button (keep pressing the alt;))

Fantastic! That did the job! Thanks a whole lot, it looks so much better.:D

---

