---
title: "Nautilus filename length"
date: 2009-05-01
forum: Desktop Environments
---

### Post by paopao on 2009-05-01
I have an "issue" with displaying long filenames in Nautilus.  When I use compact view, it truncates my filenames and replaces the ending with ... after only 12-15 characters.  I want to know if it is possible (even with some potential scripting) to change this limit to something else, say 40 characters.  Now, I know that defeats the purpose of compact view being compact, and I could use list view if I wanted to see long filenames; however, I like to see just the filenames in columns, very similar to list view as in Windows.

Is this possible?  Thanks!

---

### Post by paopao on 2009-07-05
I found a solution befitting to my problem.

Open up the run window (Alt+F2)

Type in gconf-editor

apps > nautilus > compact_view

unclick the field all+columns_have_same_width



Now, in compact view, the entire filename will be displayed, even very long names.  Effectively defeating the purpose of compact view for those who so desire.

---

### Post by arjmage on 2009-11-01
Nice.

This is what I was looking for, and works straightaway. Caveat emptor though if you like to have files with 200 characters or so.

---

