---
title: "Terminal: a way to prevent errors etc. from being printed when running CLI apps?"
date: 2009-02-05
forum: General Help
---

### Post by Piraja on 2009-02-05
Dear all,

sorry for my laziness in not searching for an answer more persistently, but is there a way of preventing error messages from being printed onto a terminal emulator while for instance editing with Nano? I mean, if I e.g. kill Conky in another terminal window, certain messages get displayed among the edited file's text. PFA an example in the screeshot.

Thanks in advance,

Piraja

---

### Post by dcstar on 2009-02-05
> **Piraja said:**
> Dear all,

sorry for my laziness in not searching for an answer more persistently, but is there a way of preventing error messages from being printed onto a terminal emulator while for instance editing with Nano? I mean, if I e.g. kill Conky in another terminal window, certain messages get displayed among the edited file's text. PFA an example in the screeshot.


Don't use TTY1, use a different one.

---

### Post by jerome1232 on 2009-02-05
You should be able to redirect it like this, standard input is 0, standard output is 1, standard error is 2

so if I wanted to redirect standard output and standard error to /dev/null (meaning just discarding it)

```
conky >/dev/null 2>/dev/null &
```

---

### Post by Piraja on 2009-02-05
Thanks to you both!

I figured out one extra way to establish this: to use gmrun (also made an icon to the launcher area of Pypanel, as seen in the screenshot).

To be honest, if I have a script to edit, I use Gedit and not Nano — so what you see in the screenshot is a sort of sham.

---

