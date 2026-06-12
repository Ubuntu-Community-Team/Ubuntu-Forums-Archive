---
title: "Help with Permissions sharing ~/Pictures/ across two users"
date: 2009-06-03
forum: General Help
---

### Post by BandD on 2009-06-03
I'm trying to share my ~/Pictures directory with my wife's account on the same machine.  Both users belong to the same group (bandd).  I created a syslink in her home direcotry that links to my ~/Pictures directory.  

I'm trying to make it so that when either of us imports photos using f-spot that we can both access those newly imported folders and that ~/.gnome2/f-spot/photos.db is shared as well (so that we can each view the updated collection in f-spot each time).

In the process I did something to the permissions that allow only root to be able to see the pictures.  Here's the output of sudo ls -l ~/Pictures

```
drwSrwS---  6 bandd bandd    4096 2009-03-03 16:57 2004
drwSrwS---  7 bandd bandd    4096 2009-02-13 15:15 2005
drwSrwS--- 13 bandd bandd    4096 2008-08-02 02:35 2006
drwSrwS--- 14 bandd bandd    4096 2009-02-13 14:35 2007
drwSrwS--- 14 bandd bandd    4096 2008-12-02 14:11 2008
drwSrwS---  8 bandd bandd    4096 2009-06-01 21:03 2009
drwSrwS---  3 bandd bandd    4096 2009-05-25 10:09 Backgrounds
-rw-rw----  1 bandd bandd 3181265 2009-06-02 15:08 img_4186-0.jpg
-rw-rw----  1 bandd bandd 3181265 2009-06-02 16:26 img_4186-1.jpg
-rw-rw----  1 bandd bandd 3181265 2009-06-02 15:06 img_4186.jpg
drwSrwS---  2 bandd bandd    4096 2009-05-12 14:58 Random
drwSrwS---  2 bandd bandd   12288 2009-06-03 13:38 Upload Stuff
```

I'm not sure where the "S" came from in the left column...

Just before this I ran a chmod 660...

Thanks for the help.

---

