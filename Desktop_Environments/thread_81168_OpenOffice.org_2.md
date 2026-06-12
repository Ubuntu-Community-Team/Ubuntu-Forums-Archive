---
title: "OpenOffice.org 2"
date: 2005-10-23
forum: Desktop Environments
---

### Post by TheIdiotThatIsMe on 2005-10-23
I just recently installed OpenOffice.org 2 (while still having 1.1.5 on my computer). When I try to boot the program I get the following error:

```
/usr/lib/openoffice2/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/usr/lib/openoffice2/program/soffice.bin: error while loading shared libraries: libvcl680li.so: cannot open shared object file: No such file or directory
```

Then it returns to the command line. Any ideas?

---

### Post by djjuice on 2005-10-24
this is how i got it to work. FIrst uninstall the old openoffice then I downloaded all the files. I used alien to convert all the rpm packages. then i installed them ran the menu installer and that worked for me.

---

### Post by abou on 2005-10-24
[quote=djjuice]this is how i got it to work. FIrst uninstall the old openoffice then I downloaded all the files. I used alien to convert all the rpm packages. then i installed them ran the menu installer and that worked for me.[/quote]I actually didn't need to run the menu editor - all it needed was a restart of X.

---

### Post by brentoboy on 2005-10-24
abou

your avitar rocks (in more ways than one)
is that megaman?

---

### Post by abou on 2005-10-24
Indeed it is, indeed it is.

---

