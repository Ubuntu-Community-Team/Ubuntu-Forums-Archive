---
title: "Don't understand picasa beta's and debian-like testing respositories"
date: 2008-12-19
forum: General Help
---

### Post by kkruecke on 2008-12-19
I want to download the picasa 3.0 beta for linux, using the google testing repositories (from [http://www.google.com/linuxrepositories/testrepo.html):](http://www.google.com/linuxrepositories/testrepo.html):)

```
# Google repository
deb http://dl.google.com/linux/deb/ stable non-free

# Google testing repository
deb http://dl.google.com/linux/deb/ testing non-free

```
Question: I know that will work with Debian, but will Ubuntu understand "testing" and "non-free"? 

Isn't "non-free" equivalent to "multiverse". So why doesn't it (for Ubuntu) say "multiverse"?

---

### Post by albinootje on 2008-12-19
> **kkruecke said:**
> I want to download the picasa 3.0 beta for linux, using the google testing repositories (from [http://www.google.com/linuxrepositories/testrepo.html):](http://www.google.com/linuxrepositories/testrepo.html):)

```
# Google repository
deb http://dl.google.com/linux/deb/ stable non-free

# Google testing repository
deb http://dl.google.com/linux/deb/ testing non-free

```
Question: I know that will work with Debian, but will Ubuntu understand "testing" and "non-free"? 

Isn't "non-free" equivalent to "multiverse". So why doesn't it (for Ubuntu) say "multiverse"?

Those are just names chosen by Google. It's no problem.

(I've used "unstable" repos from elsewhere, not Debian, but from some software project without problems.)

---

### Post by kkruecke on 2008-12-19
o.k. thanks!

---

