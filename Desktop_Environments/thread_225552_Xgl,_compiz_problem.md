---
title: "Xgl, compiz problem"
date: 2006-07-29
forum: Desktop Environments
---

### Post by JoeCool1986 on 2006-07-29
I followed pdc303's guide entitled "HowTo: Xgl + Compiz on AMD64 (Easy / Packages)" all the way until you test to make sure Xgl and compiz are present using the console. This is what I got:

```
robertlee@yoda:~$ /usr/bin/compiz --help
bash: /usr/bin/compiz: cannot execute binary file
robertlee@yoda:~$ /usr/bin/Xgl --help
bash: /usr/bin/Xgl: cannot execute binary file
```

I checked my /usr/bin directory and sure enough both the "Xgl" and "compiz" binaries are listed... I just can't execute them for some reason.

Oh, and I know my nVidia drivers are installed correctly because the nVidia logo pops up before my login. I also tried using "sudo" before the previous commands just in case and that didn't work either. I was wondering if this guide was meant for AMD64's that are actually running the 64-bit version of ubuntu, because I have an AMD64, but I'm only running the 32-bit version for compatibility reasons.

Any ideas?

---

