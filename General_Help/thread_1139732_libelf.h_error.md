---
title: "libelf.h error"
date: 2009-04-27
forum: General Help
---

### Post by grubby23 on 2009-04-27
Hi

When I am trying to include the libelf.h in my program, the output looks as follows:

In file included from type.c:3:
/usr/include/libelf.h:98: error: expected specifier-qualifier-list before ‘off64_t’
/usr/include/libelf.h:160: error: expected specifier-qualifier-list before ‘off64_t’
/usr/include/libelf.h:201: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elf_update’
/usr/include/libelf.h:207: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elf_getbase’
/usr/include/libelf.h:305: error: expected declaration specifiers or ‘...’ before ‘off64_t’
/usr/include/libelf.h:317: error: expected ‘=’, ‘,’, ‘;’, ‘asm’ or ‘__attribute__’ before ‘elf_getaroff’
type.c: In function ‘main’:
type.c:18: warning: format ‘%s’ expects type ‘char *’, but argument 3 has type ‘int’

I have seen that exactly the same issue has been reported some months ago
[https://bugs.launchpad.net/ubuntu/+source/elfutils/+bug/201078](https://bugs.launchpad.net/ubuntu/+source/elfutils/+bug/201078)

I have installed the latest libelf-dev package, but unfortunately the problem still remains. In the status of the bug it says: Triaged.

My questions is now, if there is another workaround to get this problem
solved soon? 

Many thanks for any assistance!

---

### Post by wurstmitspeck on 2009-05-04
Hello World!

I encountered the same problem. Any Solutions found yet?

Bye
wurst

gcc -o ex1 libelf_by_example_1.c -lelf
In file included from libelf_by_example_1.c:3:
/usr/include/libelf.h:98: Fehler: expected specifier-qualifier-list before »off64_t«
/usr/include/libelf.h:160: Fehler: expected specifier-qualifier-list before »off64_t«
/usr/include/libelf.h:201: Fehler: expected »=«, »,«, »;«, »asm« or »__attribute__« before »elf_update«
[...]

---

