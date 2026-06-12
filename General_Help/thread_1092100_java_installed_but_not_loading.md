---
title: "java installed but not loading"
date: 2009-03-10
forum: General Help
---

### Post by FeraTech on 2009-03-10
I am running Ubuntu Intrepid
Firefox lists 3 different java plugins. All 3 are installed and it still refuses to load java apps claiming java needs to be installed.

Any ideas?

---

### Post by Yellow Pasque on 2009-03-10
Are you using 64-bit Ubuntu by any chance? (this command will return x86_64 if you are)
```
uname -m
```

---

### Post by FeraTech on 2009-03-10
Yes sorry I forgot to mention. I am running 64-bit ubuntu.

I was able to get it running on another desktop which is also 64-bit.

---

### Post by Yellow Pasque on 2009-03-10
You should remove all the java6 and openjdk/gcj/icedtea plugins in Synaptic, and install the Java6 update 12 binary from Sun's website. Java 6u12 is the first release to feature a 64-bit browser plugin.

This is unnecessarily complicated for 64-bit users. Fortunately, Ubuntu 9.04/Jaunty has java 6u12 in the repos and installing it will be easy.

---

