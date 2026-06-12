---
title: "Fresh Texlive install - how to configure?"
date: 2009-05-15
forum: Education &amp; Science
---

### Post by Anaphylaxis on 2009-05-15
Hi! I just installed texlive and all packages through synaptic, but it didn't work straight outta the box?

> ! LaTeX Error: File `,article.cls' not found.


Strange, I didn't have to configure anything when I had debian lenny on my pc, now I am running Jaunty. Where do I find a tutorial that can teach me how to configure texlive on my ubuntu desktop properly (without reverting to debian, hehe :D ) Which config file needs to be tampered with?

---

### Post by Anaphylaxis on 2009-05-15
> **Anaphylaxis said:**
> Hi! I just installed texlive and all packages through synaptic, but it didn't work straight outta the box?



Strange, I didn't have to configure anything when I had debian lenny on my pc, now I am running Jaunty. Where do I find a tutorial that can teach me how to configure texlive on my ubuntu desktop properly (without reverting to debian, hehe :D ) Which config file needs to be tampered with?

Solved.

Had falsely included a comma in the file.
**,**article.cls

Oh, the headache.

---

