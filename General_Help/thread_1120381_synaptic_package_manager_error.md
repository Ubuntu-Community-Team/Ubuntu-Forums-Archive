---
title: "synaptic package manager error"
date: 2009-04-08
forum: General Help
---

### Post by unitc on 2009-04-08
when i try open synaptic package manager, it window comesup saying:
An error occured

The following details are provided:
E: Malformed line 56 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

---

### Post by FrankT-Qc on 2009-04-08
Could you post  line 56 of /etc/apt/sources.list

---

### Post by sekinto on 2009-04-08
Could you please post the output of this command:
```
head -56 /etc/apt/sources.list | tail -1
```

---

### Post by unitc on 2009-04-08
deb [http://giss.tv/~vale/ubuntu32](http://giss.tv/~vale/ubuntu32) .
you mean this?

---

### Post by sekinto on 2009-04-08
Did you add that to your sources.list file yourself? Because that is not the correct format for a sources.list entry.

A sources.list entry should look like this:
[type] [url] [dist] [sect(s)]
Example:
deb http://ppa.launchpad.net/do-core/ppa/ubuntu intrepid main

[type] = deb (binaries) or deb-src (source code)
[url] = location of the repository
[dist] = distribution
[sect(s)] = repository sections to include in updates (most third party repos only have main, but some have alternate sections like non-free and such)

---

### Post by FrankT-Qc on 2009-04-09
Try to replace line 56 with something like this :

```
#deb http://giss.tv/~vale/ubuntu32 .
deb http://giss.tv/~vale/ubuntu32 hardy
```

by the way, "hardy" if you're using Hardy.... This repo does not seam to have support for Intrepid...

Still, it doesn't look like a particulary well ordered repo... you might want to keep apt out of it and install the packages yourself...

---EDIT---
Actually, i didn't see any "main" section in there but still, you might also try

```
#deb http://giss.tv/~vale/ubuntu32 .
deb http://giss.tv/~vale/ubuntu32 hardy main
```

Some credible geek around here tells me that even if you don't have a "main" section in the repository, apt might expect it... You might want to give it a try if the first option doesn't work

---EDIT---

---

