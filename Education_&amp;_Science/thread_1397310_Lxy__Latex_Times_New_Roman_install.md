---
title: "Lxy / Latex Times New Roman install"
date: 2010-02-03
forum: Education &amp; Science
---

### Post by anandamide on 2010-02-03
I have a feeling this is a common question but I've looked and can't find anything. Possibly (probably) there's some glaringly obvious solution I'm missing.

I have a nicely typset report in Lyx, my first attempt at anything not in OO. The only stumbling block to being able to hand it in is the font - either Times New Roman or Arial are specifically requested in the course handbook. Is there any relatively painless way of installing TNR, without having to convert from TT font.

If not, then I'm probably going to convert it into open office, and after having seen the glorious results from Lyx I would be somewhat heartbroken!

Thanks for any advice :-)

---

### Post by Abdus on 2010-02-03
[LIST=1][*]Using TTF fonts almost directly in LaTeX is *not* that hard:
[http://www.radamir.com/tex/ttf-tex.htm](http://www.radamir.com/tex/ttf-tex.htm)

[*]There is a clone of TNR available easily:
[http://www.tug.dk/FontCatalogue/times/](http://www.tug.dk/FontCatalogue/times/)

[*]There is a clone of Arial available as well:
[http://www.tug.dk/FontCatalogue/times/](http://www.tug.dk/FontCatalogue/times/)

[*]Times New Roman is an original typeface family *designed for use in newspapers* (sic!), but Arial is not. Arial is a really flawed clone of Helvetica typeface family. Helvetica itself is also available for use in LaTeX:
[http://www.tug.dk/FontCatalogue/helvetica/](http://www.tug.dk/FontCatalogue/helvetica/)
It looks and feels better than Arial, but for an untrained eye it is *not* possible to distinguish it from Arial.

[*]If the "specific requests in the course handbook" are wrong, *don't follow them*. I never did. Required some work, but was worth the effort. Universities and companies tend to provide sets of absurd rules for typesetting documents - these rules are most often vulgar insult towards centuries of typesetting and printing wisdom. Using TNR or Arial to print a long document is an example of such absurd rule and it should not be followed. These fonts are not suited for long documents. Use Palatino (if printed) or Charter (if screened) and you will see the results are way better. You have tens of fonts available easily, and thousands available after conversion.
[/LIST]
Have fun. :)

---

### Post by anandamide on 2010-02-03
Thank you so much, you are a star! Think I'll go for the clone option.

I agree wrt daft typesetting rules, but I am not about to risk 60% of my final degree classification on the (admittedly good) chance that they won't ultimately care. I suspect it's just to prevent people writing entire essays in Comic Sans.

---

### Post by xadder on 2010-02-05
Maybe you just do:

\usepackage{times}

I'm not sure of the difference to Times New Roman, but it is pretty close I think.

---

### Post by nicolito on 2012-03-10
I know this is a solved thread, and a very old such as well. But for what it's worth I would just like to point those that wonder about the difference between Times and Times New Roman to this blog
["TypeTalk"]("http://www.creativepro.com/blog/typetalk-times-roman-vs-times-new-roman").
Although absurd, some publishers require TNR font in manuscripts. It's just a fact.

---

### Post by rewyllys on 2012-03-10
> **Abdus said:**
> . . . . If the "specific requests in the course handbook" are wrong, *don't follow them*. I never did. Required some work, but was worth the effort. Universities and companies tend to provide sets of absurd rules for typesetting documents - these rules are most often vulgar insult towards centuries of typesetting and printing wisdom. Using TNR or Arial to print a long document is an example of such absurd rule and it should not be followed. These fonts are not suited for long documents. Use Palatino (if printed) or Charter (if screened) and you will see the results are way better. You have tens of fonts available easily, and thousands available after conversion.

Have fun. :)
+1 on using Palatino.  I've done so for years, because Palatino is just simply a beautiful font!

---

