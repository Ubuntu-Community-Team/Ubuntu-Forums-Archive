---
title: "Copyleft symbol in LaTeX"
date: 2007-06-06
forum: Education &amp; Science
---

### Post by tpg on 2007-06-06
Does anybody know how to typeset a [copyleft symbol]("http://en.wikipedia.org/wiki/Copyleft") in LaTeX? Thanks in advance!

---

### Post by WW on 2007-06-06
The **textcomp** Latex package provides \textcopyleft.  For example:
```

\documentclass{article}
\usepackage{textcomp}
\begin{document}
Here is the copyleft symbol: \textcopyleft
\end{document}

```

---

### Post by tpg on 2007-06-06
Thank you WW.

---

