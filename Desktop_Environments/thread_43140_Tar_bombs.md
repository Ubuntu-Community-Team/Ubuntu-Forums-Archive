---
title: "Tar bombs"
date: 2005-06-20
forum: Desktop Environments
---

### Post by Dave_is_sexy on 2005-06-20
Oops. Why didn't my tarball work?

```
dave@D5:~/Desktop/hotwayd-0.8.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
dave@D5:~/Desktop/hotwayd-0.8.2$
```

It that a dependancies issue? Has anything happened to my system yet?

Thanks

---

### Post by derrick1985 on 2005-06-20
[QUOTE=Dave_is_sexy]Oops. Why didn't my tarball work?

```
dave@D5:~/Desktop/hotwayd-0.8.2$ ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for gawk... (cached) mawk
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
dave@D5:~/Desktop/hotwayd-0.8.2$
```

It that a dependancies issue? Has anything happened to my system yet?

Thanks[/QUOTE]


When, building software, you need compilers.

try this first:

sudo apt-get install build-essential

Then see what you get for errors. There should also be an install or readme file listing the packages you will need to compile whatever program you are trying to make.

---

### Post by Dave_is_sexy on 2005-06-20
Ah right. Cool. That's a tomorrow thing then ;)

---

