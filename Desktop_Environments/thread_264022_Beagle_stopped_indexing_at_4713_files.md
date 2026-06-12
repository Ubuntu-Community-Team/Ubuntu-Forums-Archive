---
title: "Beagle stopped indexing at 4713 files"
date: 2006-09-24
forum: Desktop Environments
---

### Post by matthias_k on 2006-09-24
Hi,

I think beagle may be broken on my system. I have over 7800 files in my home directory, but beagle is stuck at 4713 files for several weeks now. Indeed I often had the feeling that beagle didn't find files for which I knew they were there, so I fired up beagle-index-info:

```

Name: Files
Count: 4713
Indexing: True

```
So it's still indexing, but it doesn't actually proceed.

Any ideas what's going on here?

---

### Post by dexter on 2006-09-24
I'm also using beagle, here there are 142555 files indexed. He did not index them all at once though, you have to give beagle some time (a few days) to get it all done.

---

### Post by matthias_k on 2006-09-24
As I said, it has been weeks, maybe even months. That should have been enough time for beagle to index 7000 files :)

It may be because I don't had user_xattr set in fstab. I noticed that when I shut down beagle to increase its system priority, I received an error message in the log file indicating that it failed because I didn't set user_xattr on my home directory.

I'm monitoring it right now, maybe it will index my files properly now.

---

### Post by matthias_k on 2006-09-24
By the way, is it normal that Beagle keeps trying to index things which aren't there? Most entries in the schedulers are for applications that aren't even installed! (KMail, Akregator, ...).

In the log file, Beagle repeatedly tries to index my KMail inbox, which is actually non-existent, but it even logs "KMail folders not found. Will keep trying". I mean, lol.

---

### Post by matthias_k on 2006-09-24
I just noticed that beagle-shutdown doesn't work either. It has no effect at all, I waited 5 minutes, but beagled doesn't terminate. Had to kill it with -TERM.

Besides, the priority settings don't seem to work either. I set BEAGLE_EXERCISE_THE_DOG to 1 as was proposed on the beagle website when one wants more aggressive indexing. Doesn't have any effect.

I have the feeling this program is just really broken.

---

