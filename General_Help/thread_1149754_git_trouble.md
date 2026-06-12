---
title: "git trouble"
date: 2009-05-05
forum: General Help
---

### Post by marmuta on 2009-05-05
Git on my Jaunty install used to just work, but for some time I haven't been able to clone anything. There is always a "fatal: index-pack failed" but no hint of what actually went wrong. It even returns a 0 exit code, but never actually creates any files. Any ideas what I could try to get it going again? Is there some debug or verbose mode that I'm missing?

```
$ git clone git://anongit.freedesktop.org/~agd5f/drm
Initialized empty Git repository in /home/ubuntu/files/tmp/drm/.git/
remote: Counting objects: 35455, done.
remote: Compressing objects: 100% (7932/7932), done.
remote: Total 35455 (delta 27741), reused 34788 (delta 27161)
Receiving objects: 100% (35455/35455), 11.30 MiB | 215 KiB/s, done.
Resolving deltas: 100% (27741/27741), done.
fatal: index-pack failed
```

---

### Post by marmuta on 2009-05-05
Adding --local seems to have worked for some with similar problems, like ```
git clone --local --no-hardlinks git://anongit.freedesktop.org/~agd5f/drm
```

Didn't help me though, still the same index-pack failed. Any ideas?

---

### Post by marmuta on 2009-05-05
Can't get it working *shrug*. I've put it up on launchpad [lpbug]372394[/lpbug].

---

