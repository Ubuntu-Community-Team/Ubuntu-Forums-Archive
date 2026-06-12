---
title: "Latex/Kile: .cls in TEXINPUTS path yet..."
date: 2008-12-08
forum: Education &amp; Science
---

### Post by spamalot on 2008-12-08
Hello,

I need to use a .cls file and a .tex file (which contains definitions) as part of preparing an article for a journal (sim). So I've added their path to 

KILE>Settings>Configure>General>TEXINPUTS

but the new commands result in compile errors such as

.tex:18:Undefined control sequence. \received

Any suggestions?

Also in the above I have added the full path in TEXINPUTS. However, can I also just add . (current path). Path . is relative to what? Kile? The latex document?


Thanks.

---

### Post by spamalot on 2008-12-09
\documentclass{simauth} instead of \documentclass{article}

solves this problem.

---

