---
title: "curly braces dont seem to work using -regex with find"
date: 2009-03-05
forum: General Help
---

### Post by newbuntus on 2009-03-05
I have a file called messages.boot in my home folder which is matched by this:

find . -regex .*messages\.boot

but not by this:

find . -regex .*mes\{2\}ages\.boot


In the manual it says the default type of regular expressions is emacs which uses \{n\} to specify the number of times the preceding character should appear so I don't see why that won't work.

---

### Post by Brandon.Viking on 2009-03-05
Remember that the shell interprets the input line first ... you may have to escape the characters to ensure they get to find. \\\{ to prevent the shell from processing those characters.

Hope that helps.
Brandon.

---

### Post by newbuntus on 2009-03-05
You mean like \\\{2\\\} ? That didn't work by the way, but why would I need three backslashes? Also putting single quotes around like this '\{2\}' doesn't work either. Shouldn't that get past bash unchanged then?

---

### Post by Brandon.Viking on 2009-03-05
yeah the single quotes should have done it.
what that \\\ was doing is escaping using '\' for the first '\' chararter then another escape '\' then the '{'
of course single quote works and is far more readable.

you may need to specify which type of regex you are using ...s with -regextype 

man page does say that tis emacs by default. which would be '\s\2' wouldnt it?

Im not so sure, I tend to be more familiar with sed and perl.

Sorry I could not help more than that.

... I did find this to work for me....
find . -regextype posix-extended -regex '.*s{2}.*'


Regards,
Brandon.

---

### Post by newbuntus on 2009-03-05
Thanks for the help Brandon :). I had a look in the emacs manual and the syntax was as I said. I could specify the regex type like you said but I'd rather not have to write all the extra text. More importantly though it's annoying not knowing why it isn't working! Anyone else know why?

---

### Post by newbuntus on 2009-03-05
bump

---

