---
title: "Biliography in Lyx"
date: 2008-10-14
forum: Education &amp; Science
---

### Post by kokonobs on 2008-10-14
Hi,
I'm writing my report with Lyx for the first time. I'm having issues with the bibliography. Is it possible to have the bibliography arrange according to their order of appearance in the actual document? As well as have them update if i were to include a new reference and cite? I cant seem to be able to do this.
Please assist.
Thanks

---

### Post by mrgnash on 2008-10-15
Frustrations with the non-standard way that Lyx handles BibTeX was one of the reasons that I moved from Lyx to coding LaTeX by hand. 

Anyway, if you want the references in your bibliography to appear in the order cited in the document body, then you need to use the 'unsrt' Bibliography style, instead of the Lyx default (plain). I believe that Lyx has a dialog for this, or you can use ERT (evil red text) and simply type:
```
\bibliographystyle{unsrt}
```

...just before your:

```
\bibliography{file}
```

I don't really understand the second part of your question -- if you include a new reference in your BibTeX file and then cite it in the document it should appear in the reference list at the end once you recompile.

Hope that helps.

---

### Post by smartboyathome on 2008-10-15
Wow, I was just researching this today as well! Here is a good reference from the lyx team:
[http://www.karakas-online.de/mySGML/explain-bibliography.html](http://www.karakas-online.de/mySGML/explain-bibliography.html)

---

### Post by kokonobs on 2008-10-16
I did a google search and found my own post answered, amazing. 
Thanks a million mrgnash. That worked like a charm. Both questions have been answered. Thanks..

---

### Post by kokonobs on 2008-10-16
Another Question..
In the document class i am using (report), I'd prefer to call the Bibliography, References... What can i do to change it., thanks..

---

### Post by Stefan_K on 2008-10-16
Hi,

you could change it by
```
\renewcommand*\bibname{References}
```
in your document preamble.

Stefan

---

### Post by mrgnash on 2008-10-16
> **Stefan_K said:**
> Hi,

you could change it by
```
\renewcommand*\bibname{References}
```
in your document preamble.

Stefan

Thanks for helping out Stefan, I knew it would be something to do with the ever-useful \renewcommand, but wasn't sure exactly what :P

---

### Post by kokonobs on 2008-10-22
> **Stefan_K said:**
> Hi,

you could change it by
```
\renewcommand*\bibname{References}
```
in your document preamble.

Stefan

Stefan, thanks for the reply. I tried putting the code in the preamble but that did not work. 
Another website suggested putting it in the lyx document as ERT which works fine.. Thanks tho

---

### Post by xinaesthetic on 2009-03-27
edit again::: this post was pure noise; the advice in the very first reply was perfectly valid but for some reason I overlooked it as other advice was offered later.

really sorry!

---

