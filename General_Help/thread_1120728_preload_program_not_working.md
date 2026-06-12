---
title: "preload program not working"
date: 2009-04-09
forum: General Help
---

### Post by DouglasCaixeta on 2009-04-09
Hi,

I would like to use 'preload' but when I try to start it I receive the following message:

```
preload "failed reading state from /var/lib/preload/preload.state: line 8351: invalid tag"
```

On this line I have:

EXEMA32	1948	1

Which is different from the previous and the next line:

EXEMAP	32	1802	1
EXEMAP	32	1105	1

Its like is missing a parameter.
How can I solve this?
Someone use this program and can have a look on this line for me?

---

### Post by DouglasCaixeta on 2009-04-09
I try to fix the lines, or comment, but there is a lot of missing numbers.

Here is my solution:
I delete the file /var/lib/preload/preload.state

Since, even reinstalling was not fixing it.

Now, I think its working. Take a look at my /var/log/preload


```
[Thu Apr  9 11:02:54 2009] 1294180kb available for preloading, using 0kb of it
[Thu Apr  9 11:03:14 2009] 1190420kb available for preloading, using 0kb of it
[Thu Apr  9 11:03:35 2009] 1035410kb available for preloading, using 0kb of it
[Thu Apr  9 11:03:56 2009] 978850kb available for preloading, using 0kb of it
```

---

### Post by sdennie on 2009-04-09
If you delete the file in question (the .state file), it will start re-learning what to preload.  It's happened to me when I've done dramatic changes to my system and that fixed it.

---

