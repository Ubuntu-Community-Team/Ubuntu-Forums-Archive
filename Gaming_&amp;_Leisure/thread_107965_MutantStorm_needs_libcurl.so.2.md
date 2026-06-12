---
title: "MutantStorm needs libcurl.so.2"
date: 2005-12-24
forum: Gaming &amp; Leisure
---

### Post by PrincessPeach on 2005-12-24
I had an urge to play a Geometry Wars clone after watching some friends play it on their xbox 360, so I installed the [Mutant Storm demo]("http://www.pompomgames.com/mutantstorm.htm") to give it a whirl.  Unfortunately, after it's installed and I try playing it, I get this message:

```
./mutantstorm-bin: error while loading shared libraries: libcurl.so.2: cannot open shared object file: No such file or directory
```

I did an slocate for libcurl and it looks like I have libcurl3.  Is there a way to install whatever libcurl.so.2 is?

edited: edited the URL to point to the correct site.

---

### Post by Perfect Storm on 2005-12-24
Make a symblink.

```

sudo ln -s /usr/lib/libcurl.so.3 /usr/lib/libcurl.so.2

```

That should do it.

---

### Post by PrincessPeach on 2005-12-24
[QUOTE=Artificial Intelligence]Make a symblink.

```

sudo ln -s /usr/lib/libcurl.so.3 /usr/lib/libcurl.so.2

```

That should do it.[/QUOTE]

I did that and now I have this error:

```

./mutantstorm-bin: error while loading shared libraries: libstdc++-libc6.2-2.so. 3: cannot open shared object file: No such file or directory
```

---

### Post by Perfect Storm on 2005-12-24
```

sudo apt-get install libstdc++2.10-glibc2.2

```

should help

---

### Post by PrincessPeach on 2005-12-24
Thanks, that worked!

---

