---
title: "Scite - howto using apis"
date: 2009-05-09
forum: General Help
---

### Post by Manu311 on 2009-05-09
Hi,

I know I'm maybe in the wrong forum, but I have no Idea where else I could go.
My Problem is, I'm using scite and I'm very happy with it, but I want to use the advantages of the .api files, so I downloaded opengl.api and c.api from [http://www.scintilla.org/SciTEDownload.html](http://www.scintilla.org/SciTEDownload.html)
But I'm unable to include them into Scite. The FAQ don't even contain the word "api" and the documentation didn't helped me much.
I only got the line:
api.$(file.patterns.cpp)=/usr/share/scite/api/opengl.api; /usr/share/scite/api/c.api
(the files are exactly there)
and I wrote them into cpp.properties and SciTEUser.properties, but no effect.
I have no idea where my mistake is, but I hope anyone of you has.

if there's a better forum, plz move the threat ;),
thanks anyway,
Manu

---

### Post by bhagabhi on 2009-05-26
Use something like this:

```
api.*.c=/home/bhagabhi/scripts/scite/c.api
```
in your SciteGlobal.properties.

There already was a line looking like this in my version as default (commented out):
```
#api.*.cxx=d:\api\w.api
```

---

### Post by Manu311 on 2009-05-27
> **bhagabhi said:**
> Use something like this:

```
api.*.c=/home/bhagabhi/scripts/scite/c.api
```
in your SciteGlobal.properties.

There already was a line looking like this in my version as default (commented out):
```
#api.*.cxx=d:\api\w.api
```

thanks for pulling up an out dated threat just for repeating what I already did.

My version was just a little bigger:
api.$(file.patterns.cpp)=/usr/share/scite/api/opengl.api; /usr/share/scite/api/c.api

that's exactly the same (the $(file.patterns.cpp) is a string with endings like *.c and there are 2 apis at the end, because I want to apply both to those files.

---

