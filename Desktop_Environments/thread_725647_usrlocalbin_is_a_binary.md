---
title: "/usr/local/bin is a binary??"
date: 2008-03-15
forum: Desktop Environments
---

### Post by chapterthree on 2008-03-15
Anybody have any ideas on what the h*** happened here??

```
chapterthree@home:/usr/local$ ls -la bin 
-rwxr-xr-x 1 chapterthree admin 12183 2008-02-23 09:54 bin
```

How can /usr/local/bin have turned into a binary?  And how could I have survived for so long without any of the scripts under /usr/local/bin/ (unless it was just destroyed recently)?

I'm totally screwed huh.

I'm envisioning something like (without the trailing slash)```
$ cp -f somefile /usr/local/bin
```

But there's no way I would have executed something like that, especially on /usr/local/bin/.  I suspect something I installed might have done this. :(

---

