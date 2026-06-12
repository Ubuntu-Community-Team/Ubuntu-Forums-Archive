---
title: "[SOLVED] Debian Sarge, strange entries in auth.log file -- is security being compromi"
date: 2006-08-01
forum: Debian
---

### Post by RavenOfOdin on 2006-08-01
```

su [7347]: + ??? root:nobody
su [7347]: pam_unix: session opened for user nobody by (uid =0)

```

These entries have shown up twice before and I'm not quite sure what they mean since for starters the user "nobody" is disabled on my system.  Right around the last time it happened (while I was browsing these forums) Firefox went up to about 40 or so pop up windows of nothing at all and I then had to kill it.  I've been using the backported Firefox 1.5-01 from backports.org for the stable branch.

Nothing I can think of shows any user as having gained access to that account or my computer.  I have chkrootkit, rkhunter and tiger running daily and delivering mail reports to me which again say nothing major (except for that last giving me warnings that some applications in 3.1r2 of Sarge are different from those supplied with Linux 2.4.17 - which I know to not be an issue since the current and only running kernel is 2.6.x.)

I also ran applications to track the last un/successful login.  Still nothing.

I have no ports open either.

What could this be?

---

### Post by KaeseEs on 2006-08-01
I think proftpd runs as 'nobody', but I can't recall... try opening all your suspected progs, and run

```
ps aux | grep nobody
```

This should give you the culprit.

---

### Post by RavenOfOdin on 2006-08-02
Tried it. Don't see anything.

---

