---
title: "UT2004 problem on Edgy"
date: 2006-10-28
forum: Gaming &amp; Leisure
---

### Post by Rollerbob on 2006-10-28
I've just bought Unreal Tournament 2004 and I'm trying to get it working on my Ubuntu machine (AMD64, recently upgraded to Edgy).

It installs and runs fine, except I can't connect to any servers. So I've installed the Megapack (latest patch, bonus files etc) based on the instructions here: [http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml](http://www.thehaus.net/Tips/UT/ut2004icculusfaq.shtml)

Now, when I run it, I get the following error:

```
./ut2004-bin: error while loading shared libraries: ./libSDL-1.2.so.0: wrong ELF class: ELFCLASS64
```

Looks like a 64-bit architecture issue.

Can anyone help?

Matt

---

### Post by Rollerbob on 2006-10-28
Fixed. Downloaded the in the 3369-2 patch and read the FAQ properly. I hadn't done this bit: 

> rename ucc-bin-linux-amd64 to ucc-bin and ut2004-bin-linux-amd64 to ut2004-bin and you're good to go.

---

### Post by tronica on 2006-10-28
do you notice any better performance while playing that game using the 64-bit version of edgy

---

### Post by Perfect Storm on 2006-10-29
I know a diffrence in speed with the 9xxx beta nvidia driver. Much faster.

---

