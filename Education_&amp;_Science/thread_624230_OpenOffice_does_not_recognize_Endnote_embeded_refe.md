---
title: "OpenOffice does not recognize Endnote embeded references"
date: 2007-11-26
forum: Education &amp; Science
---

### Post by plvera on 2007-11-26
Hello:

I'm a recent convert to Ubuntu and I'm running it in my home PC. My lab PC, however, is still Windows (and it's unlikely to change). 

When I open my Endnote formatted word documents using OpenOffice, all the Endnote tags are missing or messed up. This presents a problem if I'm working at home and at work with the same document.

Any suggested solutions? (aside from the obvious of don't mix and match OS on important documents).

Thanks.

---

### Post by tweedledee on 2007-11-27
> **plvera said:**
> Hello:

I'm a recent convert to Ubuntu and I'm running it in my home PC. My lab PC, however, is still Windows (and it's unlikely to change). 

When I open my Endnote formatted word documents using OpenOffice, all the Endnote tags are missing or messed up. This presents a problem if I'm working at home and at work with the same document.

Any suggested solutions? (aside from the obvious of don't mix and match OS on important documents).

Thanks.

Unfortunately, there is no solution to this.  Cross-references (such as Endnote uses) can't be converted back and forth betweeen OO and Word, because apparently nobody has yet been able to work out exactly how MS is storing them in .doc format (and MS won't say), or there is some other technical limitation preventing implementation in OO.  If you must exchange electronic files with someone using Word and require references, you are unfortunately stuck with using Word.  Personally I use OO and Bibus, then just send PDFs to people who need electronic copies, but that doesn't allow for electronic edits.  You can theoretically allow for electronic edits if you "finalize" the document, so that Ednote converts the fields to raw text, but that locks out further reference manager updates and I've only had mixed success with that anyway (it works much better with Bibus).  Moreover, all my all Word+Endnote documents had to be converted to PDF (using Windows/Word) in order to keep the references, but again that largely prevents editing.  It is possible to edit a PDF, but it's not nearly as easy.

---

### Post by plvera on 2007-11-27
Thanks for the information. I was afraid it would come down to something like this.

---

### Post by ahmatti on 2007-11-30
You could use crossover office [http://www.codeweavers.com/](http://www.codeweavers.com/) to run MS office and endnote in Ubuntu, it costs 40$ but gets the job done. Or then use a virtual machine ([http://www.virtualbox.org/](http://www.virtualbox.org/)) to run windows inside Ubuntu so you can use all of your windows apps without dual booting.

I use the second option myself. I'd of course prefer not to use MS office at all, but I need electronic editing continuosly with my coauthors and several conferences require the use of word templates so I need to preserve the exact formatting. If I could just use Latex I'd be real happy :)

---

### Post by plvera on 2007-11-30
Ahmatti, thanks for your suggestions.

I'll check out the virtual box option.

---

### Post by zenkaon on 2007-12-03
you can install MS word using wine, which is free.

You could always use LaTeX and BiBTeX, which produces much better scientific documentation than word could ever dream of

---

