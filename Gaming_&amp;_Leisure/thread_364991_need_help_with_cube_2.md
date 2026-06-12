---
title: "need help with cube 2"
date: 2007-02-18
forum: Gaming &amp; Leisure
---

### Post by searayman on 2007-02-18
ok i downloaded cube 2 and tried to run it but think i am missing some dependencies.  this is what happens when i try an drun it:

mike@mike-desktop:~$ cd Desktop
mike@mike-desktop:~/Desktop$ cd sauerbraten/
mike@mike-desktop:~/Desktop/sauerbraten$ ./sauerbraten_unix 
./bin_unix/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory
mike@mike-desktop:~/Desktop/sauerbraten$ 

any ideas please, i am a begginer.

---

### Post by Perfect Storm on 2007-02-19
```
sudo aptitude install libsdl-mixer1.2
```

---

