---
title: "customize terminal prompt"
date: 2009-02-03
forum: General Help
---

### Post by JTPete on 2009-02-03
Hi All,

I am interested to find out if I can customize the prompt in my terminal.
Specifically I would like it NOT to display the complete path to the working directory as this is often quite long and I really don't like it when my commands wrap around, but I do want to still see the complete path in the title, 

any help is greatly appreciated.

---

### Post by sedawk on 2009-02-03
Some very "old style" prompt
```

export PS1="> "

```

Current path is still viewed in window title.

---

### Post by JTPete on 2009-02-03
Oh my that was easy!

Thank you, I sure wish I did not have to ask these easy questions...

---

### Post by johnl on 2009-02-03
If you want to display specific information in the prompt you can use the following escape sequences:
(more at [this link](http://www.linuxselfhelp.com/HOWTO/Bash-Prompt-HOWTO/bash-prompt-escape-sequences.html))
\u -- user
\h -- hostname
\d -- date
\t -- time
\w -- current working directory
\W -- abbreviated working directory (just the current directory)

Right now your prompt is probably set to something like:
"\u@\h:\w$ " changing it to "\u@\h:\W$ " will save you some space and still display the current directory.
(eg, "user@host:/usr/share/doc/foo-bar$"  would become "user@host:foo-bar$")

---

