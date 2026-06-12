---
title: "Dapper Opera on AMD64"
date: 2006-10-07
forum: Desktop Environments
---

### Post by cotcot on 2006-10-07
Installing Opera 9.0 was mess untill it became available in the commercial repository. I experienced it for i386. Now I changed to AMD64.
The only problem is that Opera not (yet) available for AMD 64. The commercial repo is empty for AMD64.
Does anyone has Opera 9.0 on AMD64 ? If yes how did you install it ? Thanks

---

### Post by pay on 2006-10-07
sudo dpkg -i --force-architecture opera9.deb

---

### Post by cotcot on 2006-10-07
Forcing the architecture works but I get the same mess as before the commercial repo (libqt3-mt 3.3.3 installed but asks for version 3.3.4). I get opera installed after installing version 3.3.3 but i cannot start it (/usr/bin/opera does nothing

---

### Post by pay on 2006-10-08
Run it in the terminal so we can see the error```
opera
```

---

### Post by cotcot on 2006-10-08
this is what I get running "opera"

> ERROR: ld.so: object 'libjvm.so' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object 'libawt.so' from LD_PRELOAD cannot be preloaded: ignored.
/usr/lib/opera/9.00-20060616.6/opera: error while loading shared libraries: libqt-mt.so.3: cannot open shared object file: No such file or directory


However I have libqt-mt.so;3. This is the output of locate qt-mt :
> 
/usr/lib/libqt-mt.so.3
/usr/lib/libqt-mt.so.3.3.6
/usr/lib/libqt-mt.so.3.3
/usr/share/qt3/lib/libqt-mt.so.3
/usr/share/qt3/lib/libqt-mt.so.3.3


---

### Post by basementgeek on 2006-10-08
I think you need to use the "static QT" version.  When you go to the Opera download page, click the arrow under 'select distribution and vendor' and select Other/Static DEB.  Then try sudo dpkg -i --force-architecture on that package.

---

### Post by weird_c00kie on 2006-10-12
WOOHOO! it works now! :D

thanks for that pay and basementgeek

i downloaded the "Other/Static DEB" version and forced the architecture on it and now it works perfectly fine

thanks! :)

---

### Post by basementgeek on 2006-10-12
No problem.  I was ](*,)  until I figured that out!

---

