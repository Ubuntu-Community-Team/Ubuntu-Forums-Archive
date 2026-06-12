---
title: "broken synaptic"
date: 2006-08-18
forum: Desktop Environments
---

### Post by reckless2k2 on 2006-08-18
Not sure what happened but now I get this error if I run synaptic from the terminal:

synaptic: error while loading shared libraries: libvte.so.4: cannot open shared object file: No such file or directory

Obviously, I can't run it from the GUI menu either.

Any help would be appreciated.

---

### Post by Uncle Spellbinder on 2006-08-18
This worked for me, and many others:

```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```

---

### Post by cptnapalm on 2006-08-18
the linking works as expected.

Somebody, I think, didn't check their package properly...

---

### Post by Orunitia on 2006-08-18
Nice to see I wasn't the only one affected by the update. I always love seeing quick fixes like this.

---

### Post by colonel_panic414 on 2006-08-18
I'm having a similar problem, except when I try to open Synaptic, all that happens is a prompt for my password, then nothing. I have tried using apt to reinstall it, but it doesn't help.

---

### Post by BongoBob on 2006-08-18
I had the same error after upgrading. Man you guys are fast :)

---

### Post by colonel_panic414 on 2006-08-18
Nevermind on my problem... Turns out that I'm just an idiot. I haven't tried running from the terminal and sure enough, it is exactly what you described. Applied the link and it works. <kicks self> 

lol...

---

### Post by reckless2k2 on 2006-08-19
The sym link did work perfectly. Thanks for the quick response.

---

### Post by SCD on 2006-08-19
Welcome in the Club :KS 
I was reinstall, the libvte packages with dpkg but not work. Anybody knows why? The linking works well. Thanks for the solution.

---

