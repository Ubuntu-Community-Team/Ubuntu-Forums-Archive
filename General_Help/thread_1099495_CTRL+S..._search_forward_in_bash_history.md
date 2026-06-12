---
title: "CTRL+S... search forward in bash history??"
date: 2009-03-18
forum: General Help
---

### Post by kpatz on 2009-03-18
Just a quick question.  As you all know, Ctrl+S will freeze the output on a terminal, while Ctrl-Q resumes.  But, when using EMACS mode in bash, Ctrl+S is mapped to the forward history search.  The terminal freeze overrides the bash keymapping, so I can't do a forward history search in bash.  So how do I get around this?

---

### Post by Cygnus on 2009-06-10
This seem to help:

```
stty stop undef
```

Found at: [http://nathanpowell.org/blog/archives/632](http://nathanpowell.org/blog/archives/632)

although in konsole, I still get a warning bout about output being stopped.

---

