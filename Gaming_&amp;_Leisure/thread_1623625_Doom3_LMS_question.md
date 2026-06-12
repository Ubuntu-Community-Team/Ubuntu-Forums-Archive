---
title: "Doom3 LMS question"
date: 2010-11-16
forum: Gaming &amp; Leisure
---

### Post by Gosujii-sama on 2010-11-16
After alot of work fixing sound to work properly in doom3 to begin with using Ubuntu 10.04 i come across this issue with the LMS mod when i try to load it doom3 crashes error given is:

found DLL in pak file: /usr/local/games/doom3/lms4/game_lms401.pk4/gamex86.so
copy gamex86.so to /home/jabberwock/.doom3/lms4/gamex86.so
dlopen '/home/jabberwock/.doom3/lms4/gamex86.so' failed: libstdc++.so.5: cannot open shared object file: No such file or directory

however gamex86.so DOES exist in specifyed location.... ideas?
It did work in earlyer versions of ubuntu and i would like it to work properly with this version so lemme know

---

### Post by Soulcage on 2010-11-17
libstdc++.so.5: cannot open shared object file: No such file or directory
might be your problem install it from [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") if it doesn't exsist for lucid.

---

### Post by Gosujii-sama on 2010-11-17
They really should make that better readable. It was that the libstd5 was missing but it didnt read as a missing lib it read as not being able to open the file...

---

