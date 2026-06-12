---
title: "Problems with Regnum"
date: 2007-10-15
forum: Gaming &amp; Leisure
---

### Post by Badbunny on 2007-10-15
Hello,
I followed this guide and everything went all right, up to the point where I tried to launch the game. I got a bucketful of text, of which I understood very little if that. The first line was this:
```
*** glibc detected *** ./rolauncher: free(): invalid pointer: 0x08681970 ***
```

The rest can be seen in the attached file.

I am running Kubuntu Gutsy on Intel 965 integrated graphics. Any help will be appreciated.:)

---

### Post by jaybombalous on 2007-10-16
this has already been answered else where on these forums. 

```
G_SLICE=always-malloc ./rolauncher
```

---

### Post by Badbunny on 2007-10-16
Ah, thanks. I tried to search, but apparently failed at it.

---

