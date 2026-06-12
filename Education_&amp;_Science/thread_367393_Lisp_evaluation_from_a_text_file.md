---
title: "Lisp evaluation from a text file"
date: 2007-02-22
forum: Education &amp; Science
---

### Post by mahy on 2007-02-22
Hi people,

i'm trying to enable Lisp in Ubuntu and i've already installed cmucl. I can type cmucl and start typing expression. I know it should be used within Emacs, but i'm a total Emacs noob and i don't need such a level of complexity. What i'd like to do is this: write a Lisp program (in Vim) and store it in a text file, then tell the cmucl to evaluate that text file. Is it possible? (I hope so.) Thx for any advice.

---

### Post by rickardg on 2007-02-22
You probably should look into using a lisp with readline support (clisp is the one that immediately springs to mind) or rlwrap to get a more useful REPL.

If your file is named foo.lisp you can just say 
```
* (load "foo.lisp")
``` at the REPL and lisp will evaluate your file, or you could invoke CMUCL with ```
$ lisp -load foo.lisp
```

BUT, that's not 'the lisp way'. There is really no comparison to the interactive development with emacs + [SLIME]("http://common-lisp.net/project/slime/"), at least try it out for a couple of hours. There is also [Vim-ECL]("http://wiki.alu.org/Vim_ECL"), but I don't think it's very stable yet (I haven't used it myself).

---

