---
title: "/lib/cpp fails sanaity check"
date: 2009-01-11
forum: General Help
---

### Post by Taidgh on 2009-01-11
Multiple times when I have tried to compile a program from source, I get this: ```
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.
```
The most recent example was with 'centericq'. Any idea how to fix this problem, perhaps reinstall gcc?
Here's some more info:
```
taidgh@ephedra:~/Desktop/centericq-4.21.0$ tail -10 config.log
#define PACKAGE_NAME ""
#define PACKAGE_STRING ""
#define PACKAGE_TARNAME ""
#define PACKAGE_VERSION ""
#define VERSION "4.21.0"
#endif
#ifdef __cplusplus
void exit (int);

configure: exit 1
```

---

