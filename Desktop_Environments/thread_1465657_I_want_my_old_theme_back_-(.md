---
title: "I want my old theme back :-("
date: 2010-04-29
forum: Desktop Environments
---

### Post by Egres on 2010-04-29
How I can to get my old (karmic) theme back in 10.04? I hate magenta and white instead brown and black. I don't want close button at left. Desktop icons now. Maybe this theme give more fun for others, but why was need to remove old theme completely?

---

### Post by lav0s on 2010-04-29
System > preferences > Appearance > Theme

the old themes are also there or check

[http://art.gnome.org/themes/metacity](http://art.gnome.org/themes/metacity)

---

### Post by Egres on 2010-04-30
Old ubuntu themes is missing. Human theme is almost the same, but not exactly. Icons is missed, login screen and bootlogo is missed. :-(

---

### Post by Jurjen de Vries on 2010-04-30
Thanks lav0s, that helps!

I really think ubuntu make a big mistake here in user experience. When upgraded I was not asked if I like to change my theme. After upgrade it was dark, and minimize/close buttons where moved to the left. It feels nerdy and gothic (sorry guys). Not something for a particular user.

---

### Post by infamous-online on 2010-04-30
Yeah the one thing I would like to get rid of is the close icon being on the left, how do I change it back so it goes to the right?

---

### Post by mcoleman44 on 2010-04-30
```
gconf-editor

```apps>metacity>general>button layout
```
menu:minimize,maximize,close
```

---

### Post by infamous-online on 2010-04-30
> **Jurjen de Vries said:**
> Thanks lav0s, that helps!

I really think ubuntu make a big mistake here in user experience. When upgraded I was not asked if I like to change my theme. After upgrade it was dark, and minimize/close buttons where moved to the left. It feels nerdy and gothic (sorry guys). Not something for a particular user.

It reminds of Vista going with the black theme and while it looked good it was a lil too dark for my taste.

---

### Post by infamous-online on 2010-04-30
> **mcoleman44 said:**
> ```
gconf-editor

```apps>metacity>general>button layout
```
menu:minimize,maximize,close
```

Thanks man, I appreciate the help greatly!

---

### Post by mcoleman44 on 2010-04-30
No problem :)
Remember that you will have to do that again though if you change themes.

---

