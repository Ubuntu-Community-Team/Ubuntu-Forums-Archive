---
title: "How do I change stderr text color in console"
date: 2009-06-04
forum: General Help
---

### Post by aka_bigred on 2009-06-04
How can I make them each their own color?

I want to be able to tell the difference of stdout & stderr when I'm working on the console.  If they were each different colors, it would be much easier since now it's next to impossible.

---

### Post by Coding Monkey on 2009-06-04
I am no expert, but I doubt that is possible.  As per my knowledge, stdout and stderr are simply output streams which write to the console.  The console just displays the output, without caring where it comes from.  The plain text that comes from the output stream can't have any formatting applied to it, as it is just that, plain text.

---

