---
title: "flatten folder tree (move all files that fit a given pattern to a flat directory)"
date: 2009-06-10
forum: General Help
---

### Post by godspeed_72 on 2009-06-10
I'm sure this is a common question, but I've done a bunch of searches and for the life of me I can't find an answer that works.

I have a bunch of .mp3 files in organized by "~Music/Organized/[artist name]/[album name]/[song title].mp3" (read: I let iTunes organize my music for me before switching to Linux) and I would like to move all of them into the "Music" folder.  I have seen command line solutions in OSX, but nothing in Linux.  Help?

Thanks!

---

### Post by Celauran on 2009-06-10
From within ~/Music:

```
find . -name *.mp3 -exec mv {} /home/you/Music \;
```

---

