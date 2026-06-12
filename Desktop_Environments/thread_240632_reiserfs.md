---
title: "reiserfs"
date: 2006-08-21
forum: Desktop Environments
---

### Post by fakie_flip on 2006-08-21
Hello, I'd like to know about reiserfs. What makes it better than ext3? there are several people who are using it instead of ext3. I had some problems with ext3. Deleted files are difficult to recover from ext3 even when they haven't been overwritten. I know ext2 is good about recovering deleted files, but I want something more modern. Does anyone know about reiserfs?

---

### Post by encompass on 2006-08-21
[http://www.linux.org.mt/article/filesystems](http://www.linux.org.mt/article/filesystems)
all are good... need no defraging and check themselves as they go.  At least the journalized ones do.
I use ext3.:p

---

### Post by tribaal on 2006-08-21
Hi there

Well I don't know about recovering delete files with reiserfs, but my understanding is that it is better at handling (i.e. faster) lots of small files than ext3, and so is generally more performant than ext3, except if you have large files (more than a couple of Gb).

Anyway, to make a long story short, [this]("http://en.wikipedia.org/wiki/Main_Page") is the source of most of my knowledge. You might want to look at [theses]("http://en.wikipedia.org/wiki/Filesystem") [articles]("http://en.wikipedia.org/wiki/Comparison_of_file_systems") in particular.

Cheers :)

- trib'

---

