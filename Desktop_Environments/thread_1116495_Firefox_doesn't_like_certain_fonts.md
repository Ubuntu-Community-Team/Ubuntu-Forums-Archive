---
title: "Firefox doesn't like certain fonts"
date: 2009-04-05
forum: Desktop Environments
---

### Post by smartalecks on 2009-04-05
I'm having a problem with Firefox where it doesn't seem to recognize certain fonts, both in its GTK widgets and the HTML it renders. For example, I've set "sans" to mean "DejaVu Sans," but it uses plain ol' "Sans" instead. Also, in the screenshot below, you'll see that I've set GNOME to use "DejaVu Sans Condensed" as the application font, but, again, Firefox is just using "Sans". Again, it is only certain fonts -- for example, "Courier New" (installed from the msftcore-ttf package) will work just fine.

[IMG]http://imgur.com/FBRIX.png[/IMG]

Any help is appreciated! :KS

---

### Post by smartalecks on 2009-04-05
(bump)

---

### Post by smartalecks on 2009-04-05
(bump)

---

### Post by maxinquaye on 2009-04-05
Did you set up your fonts on Edit -> Preferences -> Content Tab -> Fonts & Colours within Firefox?

---

### Post by smartalecks on 2009-04-05
> **maxinquaye said:**
> Did you set up your fonts on Edit -> Preferences -> Content Tab -> Fonts & Colours within Firefox?

Yeah, those are set to DejaVu Sans, and DejaVu Serif. I think the problem is more with the GTK widgets that Firefox uses, which I've heard it does weirdly. Specifically, I think it has to do with where Firefox is looking for the actual fonts, but then again I'm not very knowledgeable about that sort of stuff.

---

### Post by hessczoo on 2009-04-05
Hmm. Odd I can switch all the fonts around on my system without Firefox ignorning them. It must be a path confusion or something with Firefox.

---

### Post by smartalecks on 2009-04-06
Ah ha!

[http://abhinay.wordpress.com/2008/08/11/deja-vu-sans-condensed-is-working-in-firefox/](http://abhinay.wordpress.com/2008/08/11/deja-vu-sans-condensed-is-working-in-firefox/)

Thanks for the help!

---

