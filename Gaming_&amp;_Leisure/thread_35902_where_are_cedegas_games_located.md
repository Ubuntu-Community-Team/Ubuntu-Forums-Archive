---
title: "where are cedegas games located?"
date: 2005-05-20
forum: Gaming &amp; Leisure
---

### Post by dabear on 2005-05-20
Ok, so I installed steam through cedega, and it seems to work well. But when I restart my computer, where can I now find steam?

---

### Post by sethmahoney on 2005-05-20
At the terminal, type

```
cd ~/.transgaming/c_drive/"Program Files"
```

Don't forget the quotes!

---

### Post by pdk001 on 2005-05-21
how does directory has blank(like program files) move there?

---

### Post by sethmahoney on 2005-05-22
[QUOTE=pdk001]how does directory has blank(like program files) move there?[/QUOTE]
 Surround it in quotes.  Instead of typing

cd Program Files

type

cd "Program Files"

Alternatively, you can do something like

cd Pr*

and if it is the only directory there, it will cd to Program Files.

---

### Post by JonahRowley on 2005-05-23
Surround it with quotes or escape it, either way, prevent the shell from interpreting it as two arguments.  Tab completion is very useful here, Pr<tab> will complete it and escape the space for you.

---

### Post by pdk001 on 2005-05-23
awesome thanks you guys bunchs for advice
"tab" key is really useful
im feeling good to solve about worry

---

### Post by joele on 2005-05-25
can also do > cd Program\ Files

---

### Post by pdk001 on 2005-05-25
[QUOTE=joele]can also do[/QUOTE]
it doesnt work at all

---

### Post by mike998 on 2005-05-25
[QUOTE=JonahRowley]Surround it with quotes or escape it, either way, prevent the shell from interpreting it as two arguments.  Tab completion is very useful here, Pr<tab> will complete it and escape the space for you.[/QUOTE]

Ahh tab completion.  I miss it when working with windows!

---

### Post by mike998 on 2005-05-25
[QUOTE=JonahRowley]Surround it with quotes or escape it, either way, prevent the shell from interpreting it as two arguments.  Tab completion is very useful here, Pr<tab> will complete it and escape the space for you.[/QUOTE]

Ahh tab completion.  One of the best features of Bash!

---

### Post by MaX on 2005-05-31
[QUOTE=pdk001]it doesnt work at all[/QUOTE]

Yes it does. :)

---

