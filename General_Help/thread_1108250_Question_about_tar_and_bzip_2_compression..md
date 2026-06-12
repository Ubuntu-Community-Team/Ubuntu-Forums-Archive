---
title: "Question about tar and bzip 2 compression."
date: 2009-03-27
forum: General Help
---

### Post by nbtrap on 2009-03-27
Is it true that I lose no information when I compress using tar bz2?

For instance, if I compress my music directory using tar cjf, after I decompress the tar.bz2 file, will all my music retain the same quality? Most of my song files are lossless (FLAC) to begin with, and I'm afraid compressing them with tar.bz2 will taint them.

---

### Post by jespdj on 2009-03-27
Yes, [bzip2](http://en.wikipedia.org/wiki/Bzip2) is lossless compression. When you decompress a .tar.bz2 file later, you will get exactly the original data back, just like with zip and gzip.

If it were lossy, it would be useless as a general data compression scheme.

---

### Post by nbtrap on 2009-03-27
Are you sure? I just find it hard to believe. How can tar bzip2 compress an audio file without compression to a size smaller than a lossy audio compression codec can such as LAME is capable? It just doesn't make any sense, though I'm sure glad to hear it. What a tremendous amount of space I'll save!

---

### Post by jespdj on 2009-03-27
Yes, I am absolutely 100% sure. Read the Wikipedia page if you want to know the full technical details.

Suppose that it was lossy. That would mean that you could not use it to compress executable programs, word processor documents or most other kinds of data - because a program will not work anymore if you change the executable file, and word processor documents will become corrupted and unreadable if random bytes in the file were changed, etc.

If your audio files are already stored in a compressed format, you'll most likely find that those files will not compress very well when you try to compress them again with something like bzip2.

---

