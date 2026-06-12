---
title: "How to compile FBreader in user mode?"
date: 2011-12-29
forum: Desktop Environments
---

### Post by wearetheborg on 2011-12-29
I am trying to install fbreader in user mode.

Here is the Readme: see point 5
[https://github.com/geometer/FBReader/blob/master/README.build](https://github.com/geometer/FBReader/blob/master/README.build)

How do I install without being root?
It compiles fine, I only have trouble in step 5 as it needs root permission to write to 
```

install: cannot remove `/usr/share/zlibrary/encodings/Big5': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/Encodings.xml': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/GBK': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/IBM866': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-1': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-10': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-11': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-13': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-14': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-15': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-16': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-2': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-3': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-4': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-5': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-6': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-7': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-8': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/ISO-8859-9': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/KOI8-R': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/windows-1251': Permission denied
install: cannot remove `/usr/share/zlibrary/encodings/windows-1252': Permission denied
make[1]: *** [do_install] Error 1

```
An FBReader file is there in the source fbreader-0.12.10/fbreader directory, but it gives this error when I try to run it:
```
$ ./FBReader 
./FBReader: error while loading shared libraries: libzltext.so.0.13: cannot open shared object file: No such file or directory
```I have libzltext0.10 installed (the only version avaialble for Ubuntu 11.10

---

