---
title: "seeking various &quot;keyword&quot; commands"
date: 2011-08-23
forum: Desktop Environments
---

### Post by SaintDanBert on 2011-08-23
I went looking for the command **kwic** to create a keyword in context index of some text files. No joy.  

I do not find a package by that name.

I do not find anything using **apropos keyword** or **apropos context**.

A man-page for the command might look like this [http://www.thinkage.ca/english/gcos/expl/kwic.html](http://www.thinkage.ca/english/gcos/expl/kwic.html)

Output from the command might look like this
```

**Thus the input line**

cooking the wily cauliflower

**would produce output lines of the form**

cooking the wily     **cauliflower**
                     **cooking**     the wily cauliflower
     cooking the     **wily**        cauliflower

```
Variations on the output report not only these strings but the line number where that string appears in the original document. Command line options control thelength of string considered context, appearance and sort order, excluded words, output format (groff, TeX, html, &c) and other processing details.


There is a second command -- I forget the name -- that will read a text file and generate a "histogram" of the keywords. The output consists of separate lines, each line holding a word and a count. The most frequently used word appears first. The least frequently used word appears last. Command line options alter the sort order and other details of the presentation.

Thanks in advance,
~~~ 0;-Dan

---

### Post by SaintDanBert on 2011-08-25
Bump!

Someone out there must know about **kwic** indexing for linux documents.

~~~ 0;-Dan

---

### Post by jfb3 on 2011-08-25
Have you checked [http://stsdas.stsci.edu/cgi-bin/gethelp.cgi?histogram](http://stsdas.stsci.edu/cgi-bin/gethelp.cgi?histogram)
???

---

### Post by SaintDanBert on 2011-08-25
Yes, I've used that tool often  ... given the data.

I'm looking for a tool that will scan a text or similar document file
and count words:
```

prompt$  someCommand  prose.txt

the        5287
a          3123
uh         1456
quick      234
brown      156
fox          82

```

The other tool I'm seeking does the keyword index.

Cheers,
~~~ 0;-Dan

---

