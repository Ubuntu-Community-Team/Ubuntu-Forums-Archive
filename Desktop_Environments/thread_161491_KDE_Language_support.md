---
title: "KDE Language support"
date: 2006-04-17
forum: Desktop Environments
---

### Post by wabble on 2006-04-17
I want to use kde with a english user interface but supporting my norwegian text input in all kde apps so the text i type in to apps like konqueror and kopete has norwegian support and not english like the gui layout.

I have searched a bit for a quick fix, but to no luck. Is there something i have missed or is there anything i can do about it as an easy solution?

---

### Post by fdoving on 2006-04-17
Like spellchecking? Or support for æøå?

---

### Post by wabble on 2006-04-17
[QUOTE=fdoving]Like spellchecking? Or support for æøå?[/QUOTE]

Yes, spellchecking.

---

### Post by fdoving on 2006-04-17
I use aspell.

```

sudo apt-get install aspell-no

```

You can also choose to install ispell.

```

sudo apt-get install inorwegian

```

After installation you can choose what to use in Konqueror -> Settings -> Setup spellchecker (or something.. Tilpass stavekontroll på norsk). 


- Frode

---

### Post by wabble on 2006-04-19
I can't find the settings dialog you are mentioning. Is there some extra deb i have to install?

---

