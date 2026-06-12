---
title: "batch combine .mov files into a single file?"
date: 2006-09-27
forum: Desktop Environments
---

### Post by rioguia on 2006-09-27
I wanted to combine a bunch of .mov files in a directory into a single movie.  I had previously done this with .avi files by using cat and mencoder but can't find out how to do it with .mov files.  I tried this but step two threw a sementation fault:

**Step one:**
 cat DCP_0058.MOV DCP_0082.MOV DCP_0119.MOV > **one_big_movie.MOV**

**Step Two:**
B]Step two[/B]
mencoder -forceidx -oac copy -ovc copy one_big_movie.mov -o **one_big_movie.mov**

To illustrate what I am trying to do, I am showing the good results I got doing this with .avi files:

**Step one**
cat one.avi two.avi three.avi > **one_big_movie.avi**

**Step two**
mencoder -forceidx -oac copy -ovc copy one_big_movie.avi -o **one_big_movie.avi**

---

### Post by croak77 on 2006-09-27
Don't think it's possible unless you try to convert the .mov to .avi. Or maybe Quicktime Pro runs in Wine.

---

