---
title: "stupid rmdir question"
date: 2005-12-23
forum: Desktop Environments
---

### Post by ShirishAg75 on 2005-12-23
Hi all,
        is there a way to run rmdir -p recursively on child directories. Let's say I'm on a top-level directory called /home/alberto & I've a directory called mooseport which is one of the many sub-directories in my home directory. I wanna delete all the directory mooseport as well as the files & sub-directories falling under it. What would be the command for that. I know of rmdir -p --ignore fail on empty but is there a better way. I don't wanna go down a directory nor use nautilus. Looking for some command line thing. Maybe something with rm ?  I tried looking at all the mans but at a loss.

---

### Post by darth_vector on 2005-12-23
rm -r

does the trick

---

