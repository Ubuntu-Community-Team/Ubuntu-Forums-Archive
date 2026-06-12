---
title: "maxima error in texmacs"
date: 2008-04-02
forum: Education &amp; Science
---

### Post by akimatsu123 on 2008-04-02
I have maxima and texmacs installed. 

maxima was first installed, then texmacs, if that is significant at all. 

When i try to start a maxima session in texmacs, i get the error

Package 'maxima' not declared

how do i solve this problem?

I have seen instructions to change #/bin/sh to #!/bin/bash but it hasn't worked for me.

---

### Post by peterquistgard on 2008-08-07
Hey man,

What a nightmare huh? Amazing software, denied by 2 tiny bugs.

Firstly, as you said, replace "/bin/sh" with "/bin/bash" in the first line of /usr/lib/texmacs/TeXmacs/bin/maxima_detect.

Still no joy, but wait! There's more!
Edit the same file (sudo gedit /usr/lib/texmacs/TeXmacs/bin/tm_maxim)
In particular examine the case statement. You need to replace

5.11.* | 5.12.*)

with

5.11.* | 5.12.* | 5.13.*)

This will cause TeXmacs to attempt to launch Maxima 5.13 with the same command it was using for Maxima 5.12. It just so happens that this works!

Robert is your mother's brother.

---

