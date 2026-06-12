---
title: "Deleting strangely named directories with rm -rf"
date: 2009-05-05
forum: General Help
---

### Post by koffeinöverdos on 2009-05-05
Now and then I have to boot into Windows, and when I do and come back into Ubuntu, Windows has littered my external hard drive with two directories. One being $RECYCLE.BIN . I want to see if I can make a really simple script that will just rm those two directories when it mounts on bootup.

I deleted the other directory it always creates, so no problems there, but whenever I try to rm -r the $RECYCLE.BIN, it says "cannot remove `/.BIN/': No such file or directory". I would guess it isn't liking that dollar sign. I took a look at the man page and tried the workaround for files that start with a dash but it didn't work. Does anyone know how to get around that?

Thank you in advance.

---

### Post by rudy.elgato on 2009-05-05
try adding a "\" in front of the dollar sign, like:

rm -rf \$RECYCLE.BIN

---

### Post by Ugluk on 2009-05-05
$x is environment variable substitution syntax. Use ': '$RECYCLE.BIN'

---

### Post by koffeinöverdos on 2009-05-05
Rudy, worked beautifully - thank you!

---

