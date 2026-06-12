---
title: "latex-suite F9 looking in previously opened file"
date: 2007-02-07
forum: Education &amp; Science
---

### Post by fadder on 2007-02-07
I've been learning latex-suite quite happily for a week or so,
with much success. Something has gone wrong though, and
I can't work out what.   One of the great things with this vim plugin was
the completion mechanisms usin F9.  But now, when I type
\ref{sec: and hit F9, I first get lots of error messages (something
like E121:invalidCiteFile, and E15 something -- they flash by too
qickly to read), then a list of labels from another file!!

After some tests, I find that vim is looking for the last file
I opened, not the current one, when trying to do completions.

(same problem on dapper and edgy)

Help appreciated!

---

