---
title: "How do I get lyx (or bibtex) to _not_ print the &quot;note&quot; field of a bibliography item?"
date: 2010-08-18
forum: Education &amp; Science
---

### Post by bjrnfrdnnd on 2010-08-18
Well, 
the title says it all.
I try to use lyx and bibtex, but many of my bibliography items
have a field "note", containing, for example, how often the article
was cited, by whom, and so on.

When I try to use my .bib file with entries containing such "note" fields, 
the bibliography of my finished document always contains the entire "note" field. Is there a way to tell lyx/bibtex to _not_  print the note field in the references?

---

### Post by agm. on 2010-08-18
I'm not sure on using Lyx because I use Kile and basically type all of my own stuff, but I think the solution isn't really in the bibtex file but is in the "package" or "style" that you are using for citation.

For example, I use the command:
```

\usepackage{harvard}

```to define the type of bibliography (and citation commands allowed) and then at the end of my file, I have the line:

```

\bibliographystyle{agsm}

```So my recommendation is to try and figure out what bibliography style Lyx is using and see what it reports.  In this way, you should then be able to find a bibliography style that does not report the notes field when it compiles the bibtex file.

Hope this helps!

---

### Post by bjrnfrdnnd on 2010-08-19
Thannks for your reply. I tried to do it the way you are doing,
but I still get the "note" field printed out. It seems that is the default behaviour of _all_ styles.
I guess it all boils down to finding a style that ignores the "note" field.
How do I find such a style, or how do I modify a style in such a way to make it ignore the "note" field?
It is just this one modification, no fancy bibstyle-building program needed. I would want simply all 100+ styles that work in my 
installation to ignore the "note" field.

Is there a way to do this in latex/bibtex, that can be used with lyx?

Thanks a lot!

---

### Post by heterakis on 2010-09-07
In Lyx, one can use the "annote" field to add personal notes. "Annote" doesn't seem to print in the final bibliography. I'm not sure what annote may be used for, so this may conflict with the intended use of annote. You will have to edit the fields required for the types of references you use to be sure annote shows up in the input editor.


[LIST=1]
[*]Options > Customize Entry Types >
[*]Select article
[*]Under Optional fields select annote from list box
[*]Click Add
[*]Repeat for each entry type (book, booklet, conference, electronic, etc.)
[/LIST]
As you have indicated, the "note" field _will_ print in the final bibliography. Somewhat frustrating.

Sorry to find your question so late. Maybe the entry will help someone else.

---

### Post by xadder on 2010-09-08
I use the natnotes/natbib system, and notes aren't generally shown.

Another, more general, option is to use the field "comments" instead of "notes". I organise my refs and pdfs with jabref, which works with comments fine.

Failing all of that, you can always generate your own style with makebst. Use of comments is probably the simplest solution though, as it will work with all styles I have seen.

---

