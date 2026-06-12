---
title: "VIM Problem"
date: 2007-11-11
forum: Desktop Effects &amp; Customization
---

### Post by Arnitak on 2007-11-11
Idiotic question ... how to disable braces matching in VIM? :)

---

### Post by hugmenot on 2007-11-12
:help matchparen says that the command :NoMatchParen should do this, but it doesn't. You can deactivate it by issuing :set matchpairs=, though. That is, empty the list of pairs.

---

### Post by Arnitak on 2007-11-13
If I do the :set thingy the code identation dissapears. I only want the highlight matching do dissappear, not the code identation also. Any ideas?

---

### Post by aJayRoo on 2007-11-14
use this:
```
let loaded_matchparen=0
```
in your .vimrc file to disable the parenthesis matching.

---

