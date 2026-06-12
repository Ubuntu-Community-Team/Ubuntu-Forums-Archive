---
title: "Can't execute programs."
date: 2006-08-09
forum: Desktop Environments
---

### Post by Sunnz on 2006-08-09
I have just installed Edubuntu 6.06.

I can't execute anything, binaries, bash scripts, etc.

Programs that came with Edubuntu worked (bash, firefox), but not bash scripts and programs I download from WWW.

I can't execute programs that I compiled byself neither.

$ ls -l
-rwxr-xr-x 1 sunnz sunnz 23614 2005-12-09 11:44 script.sh
-rwxr-xr-x 1 sunnz sunnz 16074 2006-08-09 19:48 hello

$ ldd script.sh hello
script.sh:
        not a dynamic executable
hello:
        not a dynamic executable

$ file script.sh hello

script.sh: Bourne shell script text executable

hello: ELF 32-bit LSB executable, Intel 80386, version 1 (SYSV), for GNU/Linux 2.2.0, dynamically linked (uses shared libs), for GNU/Linux 2.2.0, not stripped

---

### Post by ardchoille on 2006-08-09
Try

./script.sh

sh script.sh

./hello

---

### Post by Sunnz on 2006-08-09
................


I was saying 'that' didn't work... (sh works, it came with edubuntu.)

```
$ ./hello
bash: ./hello: Permission denied
```

---

### Post by Sunnz on 2006-08-10
Seeing I am using this computer to do my programming school work, shall I just give up Ubuntu altogether just so things actually WORKS?

---

