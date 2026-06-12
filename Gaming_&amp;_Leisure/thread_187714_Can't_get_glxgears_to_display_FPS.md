---
title: "Can't get glxgears to display FPS"
date: 2006-06-03
forum: Gaming &amp; Leisure
---

### Post by jonboy99 on 2006-06-03
Aaargh getting frustrated - am trying to get a framerate comparison on a fresh install of dapper to compare the standard ubuntu inbuilt drivers with the ATI binaries for my radeon 9250 , but glxgears won't show a framerate  :confused: 

Googling reveals nothing to suggest any switches required etc.  There's nothing in the glxgears window apart from the graphic, and nothing comes up in the terminal window either.

Help!

Cheers
Jon

---

### Post by seth0x2b on 2006-06-03
I too don't get any FPS count in the terminal, but since I have fglrx, I use "fgl_glxgears" to see the FPS.

Cheers

---

### Post by eqisow on 2006-06-03
glxgears -printfps

---

### Post by jonboy99 on 2006-06-03
[QUOTE=seth0x2b]I too don't get any FPS count in the terminal, but since I have fglrx, I use "fgl_glxgears" to see the FPS.

Cheers[/QUOTE]

Thanks, but I want to get an fps reading before installing fglrx, and then compare with after, so need a way using standard glxgears. Maybe i need to download it as a separate package - it's part of the mesa utils and preinstalled on dapper at the moment.

---

### Post by jonboy99 on 2006-06-03
Ah, cheeers equisow.  Working great.

---

### Post by seth0x2b on 2006-06-03
Weird "problem."
I've been complaining on the forum about my low FPS count on Breezy and Dapper, in comparison with Hoary.
On Hoary I was getting above 700-800 FPS, and on Dapper I get 120-180 FPS.
Just figured the problem out: On Hoary I was using glxgears, on Dapper I always use fgl_glxgears ](*,)
As it turns out, the two apps return different values :)


Cheers

---

### Post by jonboy99 on 2006-06-03
When i try fgl_glxgears on dapper i get a spinning cube but no gears.  Is this normal?

---

### Post by seth0x2b on 2006-06-03
Yes..the fgl_glxgears test is a rotating cube.It's all normal :)

---

### Post by DoktorSeven on 2006-06-03
Amusingly enough, another, much longer switch for glxgears to do the same as -printfps is

```

glxgears -iacknowledgethatthistoolisnotabenchmark
```

:)

---

### Post by seth0x2b on 2006-06-03
> 
glxgears -iacknowledgethatthistoolisnotabenchmark



LOL

---

