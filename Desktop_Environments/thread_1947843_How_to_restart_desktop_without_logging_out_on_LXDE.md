---
title: "How to restart desktop without logging out on LXDE"
date: 2012-03-27
forum: Desktop Environments
---

### Post by tanoloco on 2012-03-27
Hello,

I had to kill all instances of PCManFM because it was hanging .. after doing that my desktop disappeared, meaning that there's no more any document or folder on my desktop and right-clicking on it will show a different context menu from the default one.

As I'm doing a batch job now which will last some hour, I was wondering if there's any command to restart my desktop without logging out.

I googled without luck :(

Thanks for any suggestion

---

### Post by ranger1021994 on 2012-03-27
U can try Alt+F2 and run pcfanman again
:) :)

---

### Post by Rodney9 on 2012-03-27
For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by tanoloco on 2012-04-12
Thank you ranger1021994,
this almost does the trick.
I found you have to press alt+f2 and type
```
pcmanfm --desktop
```

The result it's not perfect, but at least it works.

---

### Post by MG&amp;TL on 2012-04-12
It might be a good idea to kill the hung PCManFM before you start a new one-

```
killall pcmanfm
```

---

### Post by tanoloco on 2012-07-24
@MG&TL
Thanks for your headup

To complete things, a final note:
add --profile to show the default lubuntu wallpaper

so the final command is:
```
pcmanfm --desktop --profile lubuntu
```

---

