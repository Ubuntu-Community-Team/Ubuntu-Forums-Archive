---
title: "Removing complex number in Octave"
date: 2008-12-30
forum: Education &amp; Science
---

### Post by in_flu_ence on 2008-12-30
I have generated some output from a script. However, all my values have a complex number term.
E.g.
1.431333666746343+0i
4.691718399388015+0i
8.164995189955654+0i
10.03549833370017+0i
9.839658275734035+0i
9.587387724841385+0i
9.283021138629051+0i
8.845012465839011+0i

Is there a way to remove the +0i term since the real no. term is my actual result?

Solved: By writing real(data), it displays only the real no. term. Similarly, imag(data) will display the imaginary term.

---

