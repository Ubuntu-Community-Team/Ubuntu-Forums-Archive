---
title: "I need a better .pdf viewer!"
date: 2006-09-10
forum: Desktop Environments
---

### Post by PathSpace on 2006-09-10
Document viewer, the default, causes mathematical symbols to print out improperly, or even not at all.  ](*,) 

Can anyone recommend a better .pdf viewing program?

---

### Post by IYY on 2006-09-10
The official Adobe viewer can be downloaded for Linux. 

```
sudo apt-get install acroread mozilla-acroread acroread-plugins
```

I tend to use XPDF because it's faster, but it might also have problems with complex math (I never tried).

---

### Post by aysiu on 2006-09-10
IYY is right, but you have to [enable extra repositories first.](http://www.psychocats.net/ubuntu/sources)

---

### Post by arkangel on 2006-09-10
[http://www.adobe.com/products/acrobat/readstep2.html](http://www.adobe.com/products/acrobat/readstep2.html)

---

### Post by Ramses de Norre on 2006-09-10
I like kpdf better, because you can't open two instances of acroread at the same time which I think is pretty annoying. kpdf can do this though (and it prints mathematical symbols fine, I'm using it to study a maths document at the moment).

---

### Post by PathSpace on 2006-09-10
> **IYY said:**
> The official Adobe viewer can be downloaded for Linux. 

```
sudo apt-get install acroread mozilla-acroread acroread-plugins
```


Thanks for that.  :D

---

### Post by PathSpace on 2006-09-10
OK, Adobe is installed, but I can't make it print.  :( 

I've tried telling it that the print commands are /usr/bin/lp and /usr/bin/lpr.  Neither work.  :(

Can anyone help?

---

