---
title: "[SOLVED] Create relative symlinks"
date: 2008-12-22
forum: General Help
---

### Post by robz0rz on 2008-12-22
Hey all

I have a bunch of symlinks in multiple directories. Now that I transfered these directories to another system, I see how many of these symlinks are broken. This is because they are absolute symlinks that include my home directory...

How can I change all absolute symlinks in a bunch of subdirectories to relative symlinks? Thanks


**edit**
I just found out about the program *symlinks* in the repositories, but I'm not sure how to call it on each and every subdir... A bash script maybe? my bash skillz aren't that good though


**edit2**
I also just found out it can be called recursively by using a parameter -r... This was the fastest solved problem ever. I just happened to find the program after posting here. Maybe this can help someone els ein the future

---

