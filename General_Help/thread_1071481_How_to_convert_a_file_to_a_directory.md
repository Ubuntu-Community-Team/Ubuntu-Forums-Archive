---
title: "How to convert a file to a directory?"
date: 2009-02-16
forum: General Help
---

### Post by zzzuppermen on 2009-02-16
Strange question.

I have a windows network share mounted on my Ubuntu Server. When I rsync it, a single directory gives me a 'send_files failed to open "<filename>": Permission denied (13)'

If I go to the parent and issue a ```
ls -l
``` it gives me "-rwxrwSrwx" instead of "drwxrwxrwx" (windows is a pretty free world, isn't it?). I'm quite confident that it's a directory and not a file.

So. How can I change it?

Thanks!

---

