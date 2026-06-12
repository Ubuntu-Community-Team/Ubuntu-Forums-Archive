---
title: "[SOLVED] help with a quick nautilus script"
date: 2008-08-07
forum: Desktop Environments
---

### Post by fontenot_1031 on 2008-08-07
I want to create a quick script that will render all of my .tex files with pdflatex, I know that I can used the variable $NAUTILUS_SCRIPT_CURRENT_URI
to select the current folder I'm in. But what variable would I use to describe the file the script is being applied (the file I right clicked on to get to the nautilus scripts list)?

---

### Post by damoxc on 2008-08-07
How do you mean put the script?

---

### Post by fontenot_1031 on 2008-08-07
> **damoxc said:**
> How do you mean put the script?
Oops, I meant is there a variable that describes what file I right clicked on to get the nautilus scripts thing? Edited the last post. Thanks for catching that.

---

### Post by damoxc on 2008-08-07
After some playing, it seems that $1 (the first passed argument) is the file that was right clicked.

you could also do:
```

for file in $(ls); do
  some stuff
done

```

to convert every file in the current directory.

Hope this helps.

---

### Post by fontenot_1031 on 2008-08-07
> **damoxc said:**
> After some playing, it seems that $1 (the first passed argument) is the file that was right clicked.

you could also do:
```

for file in $(ls); do
  some stuff
done

```

to convert every file in the current directory.

Hope this helps.
awesome, just what I was looking for. Thank you!!

---

