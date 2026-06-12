---
title: "Using Octave and Generating HTML files"
date: 2008-07-02
forum: Education &amp; Science
---

### Post by mj-barton on 2008-07-02
I'm working on a Octave program that passes several arrays of data and it returns an HTML file with the passed data formated pretty.

My difficulty is Octave's "fprintf" command doesn't like the strings with forward(/) or backslashes(\).  Any thoughts?

---

### Post by thisismalhotra on 2008-07-03
> **mj-barton said:**
> I'm working on a Octave program that passes several arrays of data and it returns an HTML file with the passed data formated pretty.

My difficulty is Octave's "fprintf" command doesn't like the strings with forward(/) or backslashes(\).  Any thoughts?

forward and back slashes are reserved as escape sequences in most languages maybe that the case here too. See if you can somehow tell octave to ignore escape sequences.

I think a better place to post this question would be octave mailing lists.

---

