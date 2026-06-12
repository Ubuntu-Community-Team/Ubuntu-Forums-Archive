---
title: "libc6 problems"
date: 2006-07-21
forum: Desktop Environments
---

### Post by munro on 2006-07-21
I posted somthing like this yesterday and got the latest of libc6 from the ubuntu packages. Anyway, I still cannot install certain debians because of a depencendy error reguarding libc6. If I get that to go away, I have mp3 support and DVDs. My problem, I have 28k dial up on a different computer than my linux and I have to download the debians from the library and x-fer them on my flash drive. Any ideas whats wrong?

-Munro

---

### Post by bDerrly on 2006-07-21
Can you paste the error message?

---

### Post by munro on 2006-07-21
'dependency is not satisfiable: libc6'
thats it

---

### Post by bDerrly on 2006-07-21
This is the error you get when you run `dpkg -i' or...? Perhaps a reinstall of the libc package might help: `apt-get --reinstall install libc6'. I'm going to need more details to get any further.

---

