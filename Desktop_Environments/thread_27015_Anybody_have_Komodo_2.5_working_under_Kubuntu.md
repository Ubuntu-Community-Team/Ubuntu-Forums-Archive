---
title: "Anybody have Komodo 2.5 working under Kubuntu?"
date: 2005-04-14
forum: Desktop Environments
---

### Post by bnutting on 2005-04-14
I get this error message:
```

Komodo-2.5/Mozilla/mozilla-bin: error while loading shared libraries: libgdk-1.2.so.0: cannot open shared object file: No such file or directory

```
Help!

---

### Post by Klin'Targ on 2005-04-14
Hmm try doing a fresh reinstall of it. This message appears when it can't find a library it needs. 
If that doesn't work, its possible the .deb file missed the dependancy. You can try manually installing libgdk to fix it.

---

### Post by bnutting on 2005-04-14
Well here is the problem. Komodo installs via a tar ball and a install.sh script. I have tryed it on both Kubuntu and Ubuntu and I get the same error message. I personaly do not use it but I am trying to get a friend that uses it setup. I'm wondering if it is a library path issue. There is a newer version of libgdk down and usualy as long as you have version x or newer you are all set.

Thanks for the help.
Bryan

---

### Post by Klin'Targ on 2005-04-17
Sometimes tarballs are compiled against exact versions of libraries. You could try compiling it from source yourself; that would make sure it compiles against your library version.

---

### Post by tomchuk on 2005-04-17
```
apt-get install libgtk1.2
```
should take care of that. apt-file is awesome for diagnosing missing packages when compiling from source or using a binary-only app:
```

thomas@t40 % apt-file search libgdk-1.2.so.0
libgtk1.2: usr/lib/libgdk-1.2.so.0

```

---

