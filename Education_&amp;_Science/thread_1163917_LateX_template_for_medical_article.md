---
title: "LateX template for medical article"
date: 2009-05-19
forum: Education &amp; Science
---

### Post by mordecai83 on 2009-05-19
Greetings everyone,

I was wondering if anyone could point me in the direction of a good template for a medical article in lateX. I'm a med student and i just discovered LateX. Im still learning how to use it but till now i found it to be great. 

Thanks in advance

---

### Post by ad_267 on 2009-05-19
I don't think that there are really many LaTeX "templates" out there. All of the stuff you need to write an article is available in the default article class and the common packages such as natbib. For a basic article you won't really need to change much at all from the default settings, it's just things like page geometry, headers and footers, fonts and referencing which you can customise to suit your needs.

I just start with the basic article class document and over my time using LaTeX I've created my own .sty file which contains all the packages I usually use, custom commands and settings.

I've found the best guide to LaTeX is the [wikibook]("http://en.wikibooks.org/wiki/LaTeX"). If you work your way through all of that you should be pretty well set.

---

### Post by samden on 2009-05-19
By "template" I presume you mean "document class".

That depends what you are writing an article for. If it's just a generic article for an assignment or pretty well anything, the "article" class will be fine. 

If you're writing an article to submit to a journal, check with the publisher, they may already supply their own customised class file.

---

### Post by meborc on 2009-05-22
i use texworks... and their article template is great... i just add \twocolumn option after the title to make it look more professional :)

---

### Post by XCan on 2009-05-24
In principle, I think you could try using revtex (found in synaptics). It's of course mainly used for the physics society, but it should contain everything you want for a serious article no matter the field. Even though you can install it from synaptics I think it's worthwhile to take a look at the samples provided in [http://authors.aps.org/revtex4/](http://authors.aps.org/revtex4/) .

---

