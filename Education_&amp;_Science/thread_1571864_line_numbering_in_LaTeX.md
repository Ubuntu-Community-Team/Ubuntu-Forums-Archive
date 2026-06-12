---
title: "line numbering in LaTeX?"
date: 2010-09-10
forum: Education &amp; Science
---

### Post by bryncoles on 2010-09-10
Hi folks. 

I'm trying to get line numbers to show in LaTeX -- but I don't want them to appear in the margin. Rather, I'd like them to appear as part of the text body. the closest I have come to satisfaction is to put 

```
\usepackage{moreverb}
``` in the preamble, and then ```
\begin{listing}{1}
<paragraph to be numbered>
\end{listing}
```

This numbers the paragraph for me, but it uses a specialist type of the verbatim environment, and as such the fonts change. Anybody have any idea how I can add line numbers to just a paragraph, as part of the text (not in the margin) without changing the fonts?

---

