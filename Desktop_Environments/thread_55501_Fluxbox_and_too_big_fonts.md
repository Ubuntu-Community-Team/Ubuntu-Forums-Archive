---
title: "Fluxbox and too big fonts"
date: 2005-08-09
forum: Desktop Environments
---

### Post by kzu on 2005-08-09
Hi! I just installed linux yesterday and got everything to work with some little previous experience, however, I use FluxBox, and theme fonts are for some reason too big (see [here...](http://www.mbnet.fi/~tupakki/font.jpg) ) check the titlebar etc, I changed some fonts from the theme file to use the Artwiz fonts but still the titlebars font is not good and I don't want to do that for every single theme I use, so what should I try to do? May this has something to do with the fact that my computer is laptop, and maybe it installed some fonts that are good with laptops LCD screen ? Well if it's so, I don't like it.

---

### Post by SPENEN on 2005-08-09
I have the exact same problem, I've checked in the fluxbox configs but can't find anything. But I fouind out that when I run gnome-control-center and opened the font-config the font changes.
But that only works temporary and is probably not the "right" way to do it :)

---

### Post by elpresidente on 2005-08-21
I am having this problem as well. I know I must have made some change but can't remember what I was doing as I had to pack away my PC for a week just after.

---

### Post by brainv on 2005-09-02
[QUOTE=kzu]Hi! I just installed linux yesterday and got everything to work with some little previous experience, however, I use FluxBox, and theme fonts are for some reason too big (see [here...](http://www.mbnet.fi/~tupakki/font.jpg) ) check the titlebar etc, I changed some fonts from the theme file to use the Artwiz fonts but still the titlebars font is not good and I don't want to do that for every single theme I use, so what should I try to do? May this has something to do with the fact that my computer is laptop, and maybe it installed some fonts that are good with laptops LCD screen ? Well if it's so, I don't like it.[/QUOTE]


Have you installed and configured artwiz font properly?

how about running **gnome-settings-daemon** in fork.

---

### Post by plb on 2005-09-02
check to verify the fonts are indeed installed first, I've run fluxbox for about 7 years now and never had an issue with fonts......Although I always installed fonts manually. I guess I can plug my site here [www.boxwhore.org](www.boxwhore.org)  O:)  we have many fluxbox themes so check it out.

---

### Post by Juippisi on 2005-09-02
Just edit the style-file. For example:

nano ~/.fluxbox/styles/CityOfDreams/theme.cfg (or wherever your style-file is located)

Find "font" and seek for something like this:
```
menu.title.font:                                                glispbold-10
```

And change it to 

```
menu.title.font:                                                glispbold-8
```

Restart fluxbox and your menutitle should be smaller. [http://roskakori.org/files/pictures/screenshots/aterm8.png](http://roskakori.org/files/pictures/screenshots/aterm8.png) and here's a picture as an example :).

---

