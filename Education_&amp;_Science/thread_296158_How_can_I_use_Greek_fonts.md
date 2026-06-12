---
title: "How can I use Greek fonts?"
date: 2006-11-09
forum: Education &amp; Science
---

### Post by philyer on 2006-11-09
Greek fonts usually used in text about mathematics and physics, so how can I add greek fonts? 
For exmaple, I use wxmaxima, it has an option to use greek fonts, but ubuntu doesn't has any greek fonts in the English enviroment.

---

### Post by philyer on 2006-11-09
> **philyer said:**
> Greek fonts usually used in text about mathematics and physics, so how can I add greek fonts? 
For exmaple, I use wxmaxima, it has an option to use greek fonts, but ubuntu doesn't has any greek fonts in the English enviroment.
Additionally, I have install the packages of Greek in "System-Language Support".

---

### Post by boz on 2006-11-09
```
sudo apt-get install gsfonts-x11 msttcorefonts
sudo fc-cache -f -v
```

---

### Post by parktownprawn on 2006-11-09
you have to type a % sign to get a greek character.

What happens if you enter %alpha?

---

### Post by philyer on 2006-11-15
> **parktownprawn said:**
> you have to type a % sign to get a greek character.

What happens if you enter %alpha?
:( The input "%alpha" displays "%alpha", but not "&#945;".
Something I have to do before input?

---

### Post by parktownprawn on 2006-11-16
%alpha is maxima's (strange way) of inputing greek letters.

Did you install gsfonts-x11 msttcorefonts?

Try going to Edit>Configure>Style

and select "Use greek fonts"

Chose "Standard Symbols L" if you have the font installed

---

### Post by philyer on 2006-11-16
Thanks, it works in maxima.
But, additionally, how can I input greek letters in a simple text?

> **parktownprawn said:**
> %alpha is maxima's (strange way) of inputing greek letters.

Did you install gsfonts-x11 msttcorefonts?

Try going to Edit>Configure>Style

and select "Use greek fonts"

Chose "Standard Symbols L" if you have the font installed

---

### Post by parktownprawn on 2006-11-16
> **philyer said:**
> Thanks, it works in maxima.
But, additionally, how can I input greek letters in a simple text?

For what sort of application?

Try: Applications>Accessories>Character Map

I use LaTeX for writing formulae and papers.

---

### Post by parktownprawn on 2006-11-16
For entering greek in  Open Office just use a font like standard symbols l.

---

### Post by Dale Gerdemann on 2006-11-27
> **philyer said:**
> Greek fonts usually used in text about mathematics and physics, so how can I add greek fonts? 
For exmaple, I use wxmaxima, it has an option to use greek fonts, but ubuntu doesn't has any greek fonts in the English enviroment.

I believe that the default font for Ubuntu is DejaVu, which covers Greek and many other scripts. So I think your problem is not a missing font, but lack of understanding concerning input methods. The most basic input method, when all else fails is cut-and-paste. For the occasional weird character you just happen to need it's not a bad method.  For example, you want to type the symbol for "Enter Key: &#8629;. How else are you going to do it? But Greek is common enough, that your program ought to provide some input methods other than cut-and-paste. If you don't know about input methods, I highly recommend that you have a look at the Unicode editor yudit. All round it's not such a wonderful editor, but it has great input methods that are fun to play around with (and you can cut-and-paste from it if necessary). I'm really a newcomer to Ubuntu, so I don't know everything, but one other editor I've seen with half-way decent input methods is gedit. Though even in gedit I haven't seen a way to input mathematical symbols, except for good old cut-and-paste.

---

### Post by David Valentine on 2006-12-15
Another option is to add a keyboard layout.  I've added two:  U.S. international, for when I need to type accented characters, and Greek.  On Kubuntu, at least, I get a little flag in my panel that I can just click and start typing Greek letters, then click again when I want to go back to English.

---

### Post by Xiom on 2009-11-03
Can I use Ubuntu 9.10 on a Lenovo SL400 laptop?

I am considering buying a SL400 Lenovo laptop for use with Ubuntu and am studying NT Greek.

---

### Post by toallpointswest on 2009-11-23
I've run into the same problem with Maxima only that adding in the fonts and telling (wx)Maxima to use Green fonts has worked. Any other ideas?

---

