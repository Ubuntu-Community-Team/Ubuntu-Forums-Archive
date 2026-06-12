---
title: "make a cool sound, like in the movies"
date: 2009-03-22
forum: General Help
---

### Post by blazemore on 2009-03-22
Is there a way for every new line output on the terminal to make a beepy-clicky sound, like in the movies?
It would make updating more fun.

---

### Post by joey-elijah on 2009-03-22
> **blazemore said:**
> Is there a way for every new line output on the terminal to make a beepy-clicky sound, like in the movies?
It would make updating more fun.

Haha that's a crazy idea - but i love it!

---

### Post by blazemore on 2009-03-23
It must be straightforward, there's got to be a way for bash to do it, rather than a terminal program (gnome-terminal, konsole) because then it would do it when you had another tty open.

---

### Post by KeyserSoze93 on 2009-03-23
Not sure how you could make each line beep, but you could make it beep each time the prompt appeared like so:

```
PS1="\a$PS1"
```

That way, whenever it said you@yourcomputer:~$, it would beep (because \a is the escape sequence for the system bell).

---

