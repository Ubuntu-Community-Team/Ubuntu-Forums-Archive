---
title: "after you apt-get mplayer what is the url to finish configuring it ?  (wiki?)"
date: 2006-06-10
forum: Desktop Environments
---

### Post by TOPPEL on 2006-06-10
after you apt-get mplayer what is the url to finish configuring it ?  (+wiki?)

---

### Post by jazzmuzik on 2006-06-10
I don't think there's too much else except for the w32codecs package. There's the mplayer-skins package.

---

### Post by TOPPEL on 2006-06-10
the people on freenode #ubuntu have a url on how to properly configure mplayer after an apt-get install. though it might work just fine as it is ??

---

### Post by jazzmuzik on 2006-06-10
You can do a lot without the w32codecs package, but you will run into more unknown media formats. Anyway, the codecs package is part of the 'restricted' group of packages so you will need to enable the repository that contains it (either multiverse or universe, I can't remember). Then:

```
apt-get install w32codecs
```

---

### Post by TOPPEL on 2006-06-10
[QUOTE=jazzmuzik]You can do a lot without the w32codecs package, but you will run into more unknown media formats. Anyway, the codecs package is part of the 'restricted' group of packages so you will need to enable the repository that contains it (either multiverse or universe, I can't remember). Then:

[code]apt-get install w32codecs[code][/QUOTE]
they had more detailed instructions but i dont have experience with it however i will take your word that it works after an apt-get install.  i was just trying to help and spread the urls over to the forums.  it really did have more detailed mplayer configuration steps.  

take care

---

### Post by jazzmuzik on 2006-06-11
All you can do is try it. I use my own method and it works fine for me. Your link to the more detailed instructions may be great as well. Try to find out what benefits those instructions are giving you or my simple method. If it gives you more features, go for it.

---

