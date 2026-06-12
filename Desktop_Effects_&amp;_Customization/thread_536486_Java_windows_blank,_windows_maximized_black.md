---
title: "Java windows blank, windows maximized black"
date: 2007-08-27
forum: Desktop Effects &amp; Customization
---

### Post by Leon945 on 2007-08-27
I have a problem with compiz fusion..

When i have more then 3 or 4 windows open.. some of them will just go black!
depending on the size.. the bigger the windows are, the more probable they will go black apparently..

AND, i cant see Java programs.. they appear blank!

i searched around, but i cant really find a straight answer...
and there was a post about the java problem, but the links they used now point to unexistent pages...


any help?

what info should i provide?

thanks in advance

I use nvidia geforce6100

---

### Post by Grizzmo on 2007-08-29
I don't have a solution for compiz-fusion but I can confirm the exact same problem when using a gf6100.

When using Beryl I was able to fix it by selecting a different rendering path, iirc, but I've been unable to find an option for changing it (the rend.path) in compiz-fusion.


EDIT: "compiz --replace --indirect-rendering" fixes it, but I'd still prefer a tray icon solution. Fusion-icon was mentioned but didn't spot it in the reps for ubuntu.

---

### Post by TennesseeAborigine on 2007-08-29
Hey,

I've got the same thing with the hardware setup shown in my signature. I'm running feisty updated and it's a pretty fresh and very careful install. i get the black window thing running beryl. Grizzmo, how did you select the different rendering path? i would like to try that fix. 

Thanks

---

### Post by Leon945 on 2007-08-30
> **Grizzmo said:**
> 
EDIT: "compiz --replace --indirect-rendering" fixes it, but I'd still prefer a tray icon solution. Fusion-icon was mentioned but didn't spot it in the reps for ubuntu.

that seems to have fixed the black windows when maximized... thank you very much..

any info on java windows blank?

i'll loook into it myself as well...

thanks again

---

### Post by Nergar on 2007-10-22
black windows are because a driver bug in nvidia drivers, 

java problem:
```

gedit ~./bashrc
```

Add the following


```
export AWT_TOOLKIT="MToolkit"
```

---

