---
title: "Chemical Notation"
date: 2009-12-24
forum: Education &amp; Science
---

### Post by yssida on 2009-12-24
Is there any way to input standard chemical notation in word processing programs in Ubuntu? I usually make formal reports and post-labs every week so knowledge of this would be very helpful. I'm sure there must be some way to do this. Thank you very much! 

ps: what apps would you guys recommend for drawing organic structures? 3D-viewers are a plus :D :D

:D

Regards,

yssida

---

### Post by sanderd17 on 2009-12-24
If you write a lot of scientific reports I would recommend you to learn LaTeX (pronounced with the greek Chi as /&#712;l&#593;&#720;t&#603;k/). I admit, it's a weird program if you come from a word processor like Writer or Word but once the learning proces is done, it's a great help on writing reports. 

Installing LaTeX in linux can be done via synaptic and Kile is a good environment for LaTeX documents. If you want a good manual for learning LaTeX, try [The Not So Short Introduction to LATEX2&#949;]("http://tobi.oetiker.ch/lshort/lshort.pdf").

I advise you to start with LaTeX when you have enough time, it's comparable with learning to program.

Hope I helped you

---

### Post by lisati on 2009-12-24
Open Office has an option. Within OO it's File->New->Forumla or something of that nature.

---

### Post by sanderd17 on 2009-12-24
I forgot some things to say:
[LIST]
[*]if something is difficult to do in LaTeX, it will be ugly so don't do it
[*] there is also a good wikibook on LaTeX, if your learned the basics with the not so short introduction, you should take a look at [http://en.wikibooks.org/wiki/LaTeX]("http://en.wikibooks.org/wiki/LaTeX")
[/LIST]

---

### Post by yssida on 2009-12-24
@lisati: I've tried the insert formula option from OOo. It's great for math and physics notations but probably not for chemistry, but thanks anyway! :D

@sanderd17: Thank you for the link. My professors also used LaTeX in their papers and I think it would be a very powerful tool indeed. I'll try learning it by Christmas break. 

Can you give any comments on Lyx? I just downloaded it while searching for 'latex' on software centre. But anyway, I'll go install LaTeX and Kile.

Regards,

yssida

---

### Post by sanderd17 on 2009-12-24
As far as I know, LyX uses a document format that is almost like LaTeX. So it is also powerful in formula setting. There is an advantage that it's has a GUI but I think it's difficult to port it to another OS.

I know there is also a GnuTexmacs but this will neither produce TeX files. And the graphical environment is not so good as the LyX environment. 

If you change I would advise to use LaTeX as a WYWIWYG and not as a WYSIWYG program, so with an environment that lets you see the code behind it (like kile, texmaker, texnicenter for windows ...) or a simple text editor and command line.

---

### Post by yssida on 2009-12-24
I see, I downloaded TeXmaker instead of Kile since it's a smaller download. Thank you very much. Am learning the rudiments of LaTeX now.

---

### Post by SuperSonic4 on 2009-12-24
I always used to use subscript and superscript

---

### Post by sanderd17 on 2009-12-24
Did some searching on the [CTAN]("http://www.ctan.org") website(1) and I found a package made for chemical notations.

The LaTeX mhchem package(2) is in the Debian texlive-science package.

So if you install the texlive-science package from synaptic and place 
```
\usepackage[version=3]{mhchem}
```
in your LaTeX file, You can type chemical formulas with ease.

e.g.
H3O&#8314; (I don't know how to type this in a good form) but in LaTeX with the package mentionned its just 
```
\ce{H3O+}
```
 and everything stands like it should.

(1)On the CTAN website, you can find documentation of all standard LaTeX packages, [See this for documentation on the mentionned package]("http://www.ctan.org/tex-archive/macros/latex/contrib/bpchem/")
(2) Working with packages is explained in the not so short introduction.

---

### Post by yssida on 2009-12-24
Wow...this is amazing!

This means input is easier, right?

Regards,
yssida

---

### Post by sanderd17 on 2009-12-25
Yes, this means that input is easier. With LaTeX you will see that quite a lot can be done automatic. Like if you have to use the molecule CH3CH2OH a lot you can make a command for it (tis may be a stupid example because the name is more readable than the formula and therefore you will most likely use the name in your documents).

Making a command is simple it's just like
```

\newcommand{\ethanol}{\ce{CH3CH2OH}}
```

And if you now type 
```
\ethanol
```
anywhere in your document it will be shown as the chemical formula. This is in fact what packages do to. They are a collection of predefined commands.

---

### Post by esmerine on 2009-12-29
This thread encouraged me to learn LaTeX almost to the level that I'll really start learning.

---

### Post by pausut on 2009-12-29
> **sanderd17 said:**
> If you write a lot of scientific reports I would recommend you to learn LaTeX (pronounced with the greek Chi as /&#712;l&#593;&#720;t&#603;k/). I admit, it's a weird program if you come from a word processor like Writer or Word but once the learning proces is done, it's a great help on writing reports. 

Installing LaTeX in linux can be done via synaptic and Kile is a good environment for LaTeX documents. If you want a good manual for learning LaTeX, try [The Not So Short Introduction to LATEX2&#949;]("http://tobi.oetiker.ch/lshort/lshort.pdf").

I advise you to start with LaTeX when you have enough time, it's comparable with learning to program.

Hope I helped you

You could also try LyX which provides a nice front end to LaTeX

if you want chemical formula you can use something like

insert inline formula

 p, li { white-space: pre-wrap; }  $Cl_{4}^{3}$

should have the desired result,  not you need to put a space inbetween the _4 and ^3 parts,  there is a LyX mailing list for more info.


\

---

### Post by samden on 2010-01-04
Sanderd17, that is a great package. I wish I'd found that one before typing my thesis. For that I defined my own commands as you suggested above, but manually coding the formula using the mathematical commands, for example ```
\newcommand{\nitrate}{NO$_{3}^{-}$}
``` for nitrate. If you find a formula that mhchem won't do for you yssida, that will be your handiest solution if you're typing it a lot. 

But mhchem will save me a lot of hassle in future. Thanks a lot.

---

### Post by samden on 2010-01-04
Note that the documentation link posted by Sanderd17 earlier was incorrect, the mhchem documentation may be found here:
[http://mira.sunsite.utk.edu/CTAN/macros/latex/contrib/mhchem/mhchem.pdf]("http://mira.sunsite.utk.edu/CTAN/macros/latex/contrib/mhchem/mhchem.pdf")

---

