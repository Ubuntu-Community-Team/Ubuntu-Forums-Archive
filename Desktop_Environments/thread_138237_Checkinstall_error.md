---
title: "Checkinstall error"
date: 2006-03-01
forum: Desktop Environments
---

### Post by Ramses de Norre on 2006-03-01
I'm trying to compile hydrogen from source, but checkinstall gives me an error.
This is the log: ```
dpkg-deb: parse error, in file `/var/tmp/daWFFkXAVhCraieQXaoO/package/DEBIAN/control' near line 1:
 invalid package name (must start with an alphanumeric)
/var/tmp/daWFFkXAVhCraieQXaoO/dpkgbuild.log (END)

```
What does this mean? 
Just sudo make install works.

---

### Post by kaamos on 2006-03-01
there is something funny in the package name. when checkinstall gives you the list of info for the package, check what is suggests as the package name.

---

### Post by Ramses de Norre on 2006-03-01
Ok, that worked. He somehow automaticly named it .hydrogen.

But I've got another problem too: when I installed hydrogen through apt-get it didn't worked, the only sound output it gave were beeps..
So I compiled it from source hoping that would fix it but I still have that problem.. 
Do you have any idea what it could be? He says 'error starting driver' with every audio driver when I do 'restart driver'.

---

