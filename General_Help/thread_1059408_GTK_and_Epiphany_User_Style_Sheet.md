---
title: "GTK and Epiphany User Style Sheet"
date: 2009-02-03
forum: General Help
---

### Post by dbbolton on 2009-02-03
I am trying to use a custom style sheet in Epiphany, but when I uncheck "Let pages specify their own colors", Epiphany ignores my style sheet and instead grabs colors from the current GTK theme. For example, the current theme's "base" color becomes "background-color", even if i have something like:

```

body
    {
     background-color:#ff0000;
    }

```in my custom stylesheet.

Is there any way to get Epiphany to apply my style sheet to all pages and ignore their style sheets?

---

