---
title: "(SOLVED) how to create emacs tags"
date: 2009-06-12
forum: General Help
---

### Post by sa-mejia on 2009-06-12
I will here report what one needs to do to configure the TAGS file for the standard functions that emacs uses (such as mark-whole-buffer, or zap-to-char).  (I was in the process of asking for help, when an idea occurred to me, which ended up working, I am here writing down how it did work to save some people the burden of figuring it out themselves).

I am running Ubuntu Hardy.

1.  Install from the repository the package emacs22-el (which has the source files).

2.  Open an emacs session as a sudo user.  ($ sudo emacs).

3.  Within emacs, type M-x cd RET /usr/share/emacs/22.1/lisp/

4. M-x compile RET etags *.el.gz

5. You are done.  The first time you try to run find-tag, emacs will ask for the location of the TAGS file is (/usr/share/emacs/22.1/lisp/TAGS)


I basically followed the steps in "An Introduction to Programming in Emacs Lisp", in particular the instructions in: chapters 4.1 Finding More Information; and 12.5 Create Your Own `TAGS' File.  

However, in those instructions, they mention that you compile by calling etags *.el.  The repository downloads the source files, however, not in his format, but zipped, which is why one has to compile, not the *el files, but the *.el.gz files.  

I hope this might help others.

Santiago Mejia.

---

