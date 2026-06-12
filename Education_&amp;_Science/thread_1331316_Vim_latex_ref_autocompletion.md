---
title: "Vim latex \ref autocompletion"
date: 2009-11-19
forum: Education &amp; Science
---

### Post by semperfizh on 2009-11-19
Hi there,

It seems that there are some issues with vim latex on ubuntu.

I have the following problem.
Completion of \ref tags isn't working for me. Upon pressing F9,
it shows the list of labels to choose from, 
but when I press enter, I get the following error:

E172: Only one file name allowed.

(I assume it has something to do with python.)

Any suggestions?

Thanks.

---

### Post by arg_khs on 2011-03-21
Hi,

I have the same problem. In my case it was that the folder in which I was working included a space in the name. Apparently there is an error in how python is called according to this thread 

[http://www.mail-archive.com/vim-latex-devel@lists.sourceforge.net/msg00511.html](http://www.mail-archive.com/vim-latex-devel@lists.sourceforge.net/msg00511.html)

My solution was to install the latest version of vim-latex suite from sourgeforge.net.

Hope this helps.

---

