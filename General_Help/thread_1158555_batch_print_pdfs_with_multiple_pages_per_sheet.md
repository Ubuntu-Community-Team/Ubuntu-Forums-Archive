---
title: "batch print pdfs with multiple pages per sheet?"
date: 2009-05-13
forum: General Help
---

### Post by lavinog on 2009-05-13
I am printing a bunch of pdf documents.
I want to print them 2 pages per side, front and back.

So far I have come up with this command:
```

IFS='
'
for x in *.pdf;do lp -o sides=two-sided-long-edge "$x";done
unset IFS

```
but I can't seem to get 2 pages per side.

I suspect that ghostscript has a way to do this. Does anyone know how?

---

