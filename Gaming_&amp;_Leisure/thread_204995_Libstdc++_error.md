---
title: "Libstdc++ error"
date: 2006-06-27
forum: Gaming &amp; Leisure
---

### Post by Blazeix on 2006-06-27
I'm trying to run nexiuz (a linux game). It installed fine, but when I try to run it I get this error:
error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory.

I have libstdc++6 installed, and I searched around and it appears I need this package: compat-libstdc++. However, I cannot seem to find it for Ubuntu. Can anyone help? Thanks.

---

### Post by Footissimo on 2006-06-27
Have you got libstdc++5 installed?  Try a:
```
sudo apt-get install libstdc++5
```

If it is installed then you could locate the libstdc++.so.5 file then do a symbolic link

---

### Post by Blazeix on 2006-06-27
Thank you so much! Simply installing libstdc++5 worked. I assumed that having the latest version would be the best, but I guess I still have a lot to learn!

---

