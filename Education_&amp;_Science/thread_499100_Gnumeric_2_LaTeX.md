---
title: "Gnumeric 2 LaTeX?"
date: 2007-07-12
forum: Education &amp; Science
---

### Post by Schoappied on 2007-07-12
Hi,

In Openoffice Calc. You've a macro which makes it possible to 'convert' a table to LaTeX ([http://calc2latex.sourceforge.net/](http://calc2latex.sourceforge.net/)). This is also possbible in Msoffice Excel.

Now I'm wondering if there's also a macro like that in GNUMERIC?

Please share Your knowledge! ;)

---

### Post by xadder on 2007-07-13
I don't use gnumeric so much, but isn't it easy to just save as comma separeted and use a little shell scripting from there, e.g. 


```

 sed "s/,/\&/" table.csv  | awk '{print $0 "\\\\"}'

```

sed converts the commas (or semicolons or whatever) and awk just adds the \\ which are needed.

---

### Post by radiobuzzer on 2011-10-26
No it is not the same, because this way you are loosing the merged cell and other decorative information.

---

### Post by nothingspecial on 2011-10-26
This thread is old and consequently rather moldy.

It needs burying again.

Closed.

---

