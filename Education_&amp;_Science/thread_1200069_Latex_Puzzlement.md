---
title: "Latex Puzzlement"
date: 2009-06-29
forum: Education &amp; Science
---

### Post by DBQ on 2009-06-29
Hi everybody. I am writing something in latex, and feel frustrated with bibtex. I use this code in the bib file:

[code]
@MISC{VirtualPC,
title = "VirtualPC",
url = {http://www.microsoft.com/windows/products/winfamily/virtualpc/},
}
[\code]

However, the only thing that shows up is: Virtualpc.  Any pointers? Thank you guys in advance.

---

### Post by XCan on 2009-06-29
That would depend on what you've set your bibliographystyle to. Some styles won't output the url flags, well actually most styles don't. You can generate your own style and customize it using bibit (in synaptics).

---

### Post by DBQ on 2009-06-29
The style I use is plain.  It seems to output URLs just fine for other citations, but not this one.

---

### Post by unutbu on 2009-06-29
Perhaps there is an invisible character which is messing things up.

How about try this:

Comment out 

```
% @MISC{VirtualPC,
% title = "VirtualPC",
% url = {http://www.microsoft.com/windows/products/winfamily/virtualpc/},
% }
```

copy in its place any of the other bib entries with a url that works.
Slowly edit that entry until it matches the above. (i.e., change the @MISC line first, then update the title, then part of the url then the rest of the url.) Keep running latex each time to check that the url shows up.

---

### Post by hugmenot on 2009-06-30
You can use MISC with howpublished:

```
howpublished = {\url{http://www.microsoft.com/windows/products/winfamily/virtualpc/}},
```

or MANUAL with 

```
note = {available online at \url{http://www.microsoft.com/windows/products/winfamily/virtualpc/}}
```

---

### Post by DBQ on 2009-06-30
Thank you guys.  I tried hugmenot's suggestion and it seemed to work - although I had to remove the \url part (it seemed to produce some strange spaces).  

I still feel puzzled as to why this is happening.  I use exactly the same citation types in other places in the bibliography and they work just fine.

---

### Post by meborc on 2009-06-30
maybe the "\" is making the problems?? is \url a command? if not, use $\$url instead

---

### Post by hugmenot on 2009-06-30
> **DBQ said:**
> Thank you guys.  I tried hugmenot's suggestion and it seemed to work - although I had to remove the \url part (it seemed to produce some strange spaces).  

I still feel puzzled as to why this is happening.  I use exactly the same citation types in other places in the bibliography and they work just fine.

What do you mean with "the same"? That you use MISC entries with the plain.bst bibliography style and it prints the URL field out? I find this surprising because plain.bst doesn&#8217;t look at the url field.

Just inspect it:
```
gedit `kpsewhich plain.bst`
```


[The TeX FAQ]("http://www.tex.ac.uk/cgi-bin/texfaq2html?label=citeURL") advises this technique also.

---

### Post by hugmenot on 2009-06-30
> **meborc said:**
> maybe the "\" is making the problems?? is \url a command? if not, use $\$url instead

Why reply if you have no idea what&#8217;s going on?

---

### Post by meborc on 2009-06-30
> **hugmenot said:**
> Why reply if you have no idea what’s going on?

sorry :) misread 2 threads... not a morning person

replied cuz i thought i had an answer, if i had known i had no idea, i would have not answered - logical, kind of

ignore me!

---

