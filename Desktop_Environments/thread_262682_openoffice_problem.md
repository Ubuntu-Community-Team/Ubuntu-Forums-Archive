---
title: "openoffice problem"
date: 2006-09-22
forum: Desktop Environments
---

### Post by kellykamay on 2006-09-22
/usr/lib/openoffice/program/javaldx: error while loading shared libraries: libuno_sal.so.3: cannot open shared object file: No such file or directory
/usr/lib/openoffice/program/soffice: line 233:  5867 Segmentation fault      "$sd_prog/$sd_binary" "$@"

** (process:5853): WARNING **: Unknown error forking main binary / abnormal early exit .

i got this problem whenever i run my openoffice..pls help me to solve this

---

### Post by kellykamay on 2006-09-22
hehehe...problem solved!!

here's what i did, by using synaptic package manager i search all openoffice.org and openoffice.org2 files(and other files such openoffice.org-writer,openoffice.org-base etc..) and mark them as complete removal..then apply

after that i erased my .openoffice.org2/ directory with rm -rf

then a fresh new install $ sudo apt-get install openoffice.org2

and viola!!! its working now..

thank u for reading,,peace!!

---

