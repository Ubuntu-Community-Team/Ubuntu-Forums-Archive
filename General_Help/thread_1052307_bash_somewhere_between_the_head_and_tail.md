---
title: "bash: somewhere between the head and tail"
date: 2009-01-27
forum: General Help
---

### Post by alphaniner on 2009-01-27
Is there a bash command which can output a specified range of lines (ie. line 5 or lines 9-16) from a file?  Like head or tail, but in the middle.  And no, it's not body or torso unfortunately.

---

### Post by estyles on 2009-01-27
Use a combination of head and tail with a pipe command.  I'm not an expert on pipes, and am not on linux right now to check, but it should be something like:

head -n 16 blah.txt | tail -n 8

to print lines 9-16

---

### Post by alphaniner on 2009-01-27
Yea, I realized that shortly after I made the post.  I was hoping for a more straightforward way, but really, this works just fine.  Thanks.

edit: how do I mark a thread as solved?  It doesn't seem to be in Thread Tools anymore.

---

### Post by snova on 2009-01-27
> **alphaniner said:**
> edit: how do I mark a thread as solved?  It doesn't seem to be in Thread Tools anymore.

Temporarily disabled; see: [http://ubuntuforums.org/showthread.php?t=1039481](http://ubuntuforums.org/showthread.php?t=1039481)

---

### Post by stylishpants on 2009-01-27
Use sed.

```

# print lines 2-4 inclusive
sed -n '2,4p' file.txt

# print line 3
sed -n '3p' file.txt


```

---

### Post by alphaniner on 2009-01-27
sed makes my brains hurt XO.  Or trying to learn it at least.  Thanks.

---

