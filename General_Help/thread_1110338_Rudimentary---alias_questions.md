---
title: "Rudimentary---alias questions"
date: 2009-03-29
forum: General Help
---

### Post by Rujiel on 2009-03-29
Where's the cleanest place to throw the folder of a new executable? Is it generally advised to simply throw the directory in bin and make an alias for it?

If I were to just throw it in my user home and make an alias calling an exec in the directory from there, would linux know the next time I use that alias that I'm referring to an exec in a totally different dir, or would I have to be explicit about the dir each time I use the alias?

---

### Post by cariboo on 2009-03-29
Normally programs that you install or compile your self should go in /usr/local for folders and /usr/local/bin for programs. You don't have to create any aliases as /usr/local is in your path.

Jim

---

### Post by Rujiel on 2009-03-31
How do I make the executable named x callable anywhere? Throwing its folder (it has necessary support files) in usr/local/bin?

---

