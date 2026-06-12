---
title: "Bareword &quot;svg&quot; not allowed"
date: 2006-11-28
forum: Desktop Environments
---

### Post by Bob_Mendon on 2006-11-28
I was trying to rename the trashcan_full.svg to trashcan_full.xxx so I could replace the trashcan icon with another one. When I did, I got the following error: 

[COLOR="Blue"]Bareword "svg" not allowed while "strict subs" in use at (eval 1) line 1.
[/COLOR]
Any idea what this means??? I tried a google search and came up with people asking the same question and no real answer.

---

### Post by flugh on 2006-11-28
What was the -exact- command you ran to get this output?

---

### Post by Joe_CoT on 2006-11-28
See [this page](http://perldoc.perl.org/strict.html#'strict-subs')

Which means that it's a perl error, and a bug in the program you're using to rename. Perl programs should always be using strict, so it really isn't a problem on your end :-k Have you tried renaming it from a console?

```

cd that/directory
sudo mv trashcan_full.svg trashcan_full.xxx
```

---

### Post by Bob_Mendon on 2006-11-29
It worked from the console! Thanks.

---

