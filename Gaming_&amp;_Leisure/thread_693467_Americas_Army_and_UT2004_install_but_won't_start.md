---
title: "Americas Army and UT2004 install but won't start"
date: 2008-02-11
forum: Gaming &amp; Leisure
---

### Post by nixHead23 on 2008-02-11
Hi first post, been checking out Ubuntu for a while and decided to take the plunge and dedicated my entire mac mini hard drive to it. Setup has been good so far. Just have a snag with the UT game engine I think.  Neither the Americas Army or the UT2004 game with start. Both installed just fine but seem to be lacking a library or something.

user@ubuntu:~$ armyops 
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory 
user@ubuntu:~$ 



both games get the same message about not finding  libstdc++.so.5.

Has anyone see this before? (I have been searching the forum and google  no luck)

Any help would be appreciated



[HEY THANKS! wORKED LIKE A CHARM! :) ]

---

### Post by Perfect Storm on 2008-02-11
```
sudo aptitude install libstdc++5
```

Should do it

---

