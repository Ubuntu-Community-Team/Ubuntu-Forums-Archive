---
title: "LaTeX PGF CVS"
date: 2009-12-04
forum: Education &amp; Science
---

### Post by kbaumen on 2009-12-04
Hi

I've installed PGF on my Ubuntu from the standard repositories, which gives the version 2.00. That doesn't include some of the latest libraries from [COLOR=Blue]_[here]("http://www.texample.net/tikz/builds/2009/06/02/a/")_[/COLOR]. I am particularly interested in the circuits libraries. I tried downloading them and copying manually into the library folder (/usr/share/texmf/tex/generic/pgf/frontendlayer/tikz/libraries), however the pdfTex can't find those libraries.

Can someone please give me some pointers on what to do? This is quite important for me.

Cheers.

---

### Post by kbaumen on 2009-12-06
Problem solved.

---

### Post by samden on 2009-12-06
Please say how you solved it. Remember others with the same problem will search for answers and reach your thread, this will help others in future. If you found the answer elsewhere, post a link to it.

---

### Post by kbaumen on 2009-12-07
> **samden said:**
> Please say how you solved it. Remember others with the same problem will search for answers and reach your thread, this will help others in future. If you found the answer elsewhere, post a link to it.

Well, technically I didn't solve it but you're right anyway. I found a package called Circuitikz, which works fine for me. Graphics are quite good. Tikz commands work inside the circuitikz environment. It can be found _[COLOR=Blue][here]("http://home.dei.polimi.it/mredaelli/circuitikz/index.html")[/COLOR]_. My only complaint about it would be that the logic gates have a limitation of two inputs (at least I didn't find anywhere in the manual anything about more inputs). But alltogether, a really nice package.

---

