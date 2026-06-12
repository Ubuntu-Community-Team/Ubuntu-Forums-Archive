---
title: "Generating citation text from BibTeX within a LaTeX document"
date: 2010-02-26
forum: Education &amp; Science
---

### Post by WebDrake on 2010-02-26
Hello all,

Now, we all know and love LaTeX and BibTeX.  One thing I've never worked out how to do: is there a command by which one can generate the (full or partial) citation text WITHIN a document?

I'm thinking of for example the case where I might want to have a citation in an abstract, e.g.

[INDENT]Recent results on the sprogget of nurdle [A.B. Ceedee et al., Noggin Review 43(2): 22-45] have indicated that I need to learn how to use LaTeX better...[/INDENT]

Or alternatively of the case where I might want to have several citations under one number, and have a BibTeX entry along the lines of,

```
@misc{severalrefs,
    note="\fullcitation{ref1}; \fullcitation{ref2}; fullcitation{ref3}"
}
```

Is there any way to achieve this?

Thanks & best wishes,

    -- Joe

---

### Post by WebDrake on 2010-03-04
No answer to the general problem, but in terms of generating multiple citations, this turns out to be very useful:
[http://ctan.tug.org/tex-archive/macros/latex/contrib/mciteplus/](http://ctan.tug.org/tex-archive/macros/latex/contrib/mciteplus/)

---

