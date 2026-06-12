---
title: "What happened to the fps readout on glxgears"
date: 2006-01-05
forum: General Help
---

### Post by bannerboy on 2006-01-05
Where did it go, when I was running gentoo, glxgears always gave me output like this:

```
31726 frames in 5.0 seconds = 6345.200 FPS
```

but when I switched to kubuntu, and ran glxgears, there was no fps readout, where did it go?

---

### Post by dmh-bidlah on 2006-01-05
You have to run glxgears as ```
glxgears -iacknowledgethatthistoolisnotabenchmark
```

---

### Post by bonzodog on 2006-01-05
alternatively,
```
 $glxgears -printfps
``` 
works just as well

---

### Post by bannerboy on 2006-01-05
out of curiosity, why does it have that option?

---

