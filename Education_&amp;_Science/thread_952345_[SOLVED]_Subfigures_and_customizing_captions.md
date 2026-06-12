---
title: "[SOLVED] Subfigures and customizing captions"
date: 2008-10-19
forum: Education &amp; Science
---

### Post by ad_267 on 2008-10-19
I've been using ccaption to make my captions italic in LaTeX but I've just tried to use subfig for subfigures and the two packages won't work together.

How can I modify the caption font when using subfigures? I tried using "\renewcommand\captionfont{\itshape}" as subfig says it works with the caption package, but this doesn't have any effect.

---

### Post by ad_267 on 2008-10-19
Never mind, I figured it out. I loaded the caption and subfig packages like this:

```
\usepackage[labelfont=it,textfont=it]{caption}
\usepackage{subfig}
```

---

### Post by jlinkels on 2013-01-27
First hit in Google for this problem. Thanks for posting.

jlinkels

---

### Post by nothingspecial on 2013-01-27
Old thread.

Closed.

---

