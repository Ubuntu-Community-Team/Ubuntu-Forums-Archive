---
title: "RTCW on 64-bit system?"
date: 2007-09-11
forum: Gaming &amp; Leisure
---

### Post by Luksion Knight on 2007-09-11
is there a way to install return to castle wolfenstein on a 64-bit system? all the binaries are for 32-bit.

---

### Post by Cappy on 2007-09-12
It will work fine. You will probably need
```
sudo apt-get install ia32-libs ia32-libs-sdl
```

If it requires more libraries than that you can use getlibs:
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by Luksion Knight on 2007-09-12
well when i try to run it (its a .run file by the way) i get this error in terminal:
```
./setup.sh: 20: source: not found
This installation doesn't support glibc-2.0 on Linux / x86_64
(tried to run setup)
Fatal error, no tech support email configured in this setup
The setup program seems to have failed on x86_64/glibc-2.0
```

---

### Post by Cappy on 2007-09-12
Try ```
sudo apt-get install libc6-i386
```

---

### Post by Luksion Knight on 2007-09-12
says its already installed.

---

### Post by Cappy on 2007-09-13
```
sudo apt-get install linux32
```

```
linux32 sh yourfilename.run
```


If you are missing any further libraries try this:
Install getlibs from here: [http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
and then run this:
```
sudo getlibs -32 libglib-2.0.so.0 libstdc++-libc6.2-2.so.3
```

---

### Post by Luksion Knight on 2007-09-13
```
./setup.sh: 20: source: not found
The setup program seems to have failed on x86/glibc-2.0

Fatal error, no tech support email configured in this setup
The program returned an error code (1)

```

same error as last time :(
i think it may just be downright glibc incompatibility. thanks for trying.

---

