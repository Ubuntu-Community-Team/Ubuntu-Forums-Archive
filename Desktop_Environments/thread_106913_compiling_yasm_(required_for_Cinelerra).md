---
title: "compiling yasm (required for Cinelerra)"
date: 2005-12-21
forum: Desktop Environments
---

### Post by mepapp on 2005-12-21
I'm attempting to compile Cinelerra, which requires nasm, yasm, and a whole host of other things. I've gotten nasm through apt, but yasm doesn't seem to be there. It also has no hits when searching for yasm on this forum, which worries me. 

after running autoget.sh, and then ./configure I run make.

Here's the compile error:

```

spool@quark:~/apps/yasm$ make
gcc   -c -o re2c-main.o `test -f tools/re2c/main.c || echo './'`tools/re2c/main.c
In file included from tools/re2c/main.c:4:
tools/re2c/globals.h:4:31: error: tools/re2c/basics.h: No such file or directoryIn file included from tools/re2c/main.c:5:
tools/re2c/parse.h:5:32: error: tools/re2c/scanner.h: No such file or directory
tools/re2c/parse.h:6:27: error: tools/re2c/re.h: No such file or directory
In file included from tools/re2c/main.c:5:
tools/re2c/parse.h:10: error: syntax error before ‘Str’
tools/re2c/parse.h:10: warning: no semicolon at end of struct or union
tools/re2c/parse.h:11: warning: data definition has no type or storage class
tools/re2c/parse.h:12: error: syntax error before ‘}’ token
tools/re2c/parse.h:12: warning: data definition has no type or storage class
tools/re2c/parse.h:14: error: syntax error before ‘*’ token
tools/re2c/parse.h:15: error: syntax error before ‘*’ token
tools/re2c/parse.h:15: error: syntax error before ‘*’ token
tools/re2c/parse.h:15: warning: data definition has no type or storage class
tools/re2c/parse.h:16: error: syntax error before ‘*’ token
tools/re2c/parse.h:16: error: syntax error before ‘*’ token
tools/re2c/parse.h:16: warning: data definition has no type or storage class
tools/re2c/parse.h:21: error: syntax error before ‘*’ token
tools/re2c/parse.h:22: error: syntax error before ‘*’ token
tools/re2c/parse.h: In function ‘Symbol_new’:
tools/re2c/parse.h:24: error: ‘r’ undeclared (first use in this function)
tools/re2c/parse.h:24: error: (Each undeclared identifier is reported only once
tools/re2c/parse.h:24: error: for each function it appears in.)
tools/re2c/parse.h:25: error: ‘str’ undeclared (first use in this function)
In file included from tools/re2c/main.c:6:
tools/re2c/dfa.h: At top level:
tools/re2c/dfa.h:37: error: syntax error before ‘RegExp’
tools/re2c/dfa.h:37: warning: no semicolon at end of struct or union
tools/re2c/dfa.h:37: warning: no semicolon at end of struct or union
tools/re2c/dfa.h:38: warning: data definition has no type or storage class
tools/re2c/dfa.h:39: error: syntax error before ‘}’ token
tools/re2c/dfa.h:39: warning: data definition has no type or storage class
tools/re2c/dfa.h:41: error: syntax error before ‘*’ token
tools/re2c/dfa.h:57: error: syntax error before ‘RegExp’
tools/re2c/dfa.h:57: warning: no semicolon at end of struct or union
tools/re2c/dfa.h:62: error: syntax error before ‘*’ token
tools/re2c/dfa.h:62: warning: data definition has no type or storage class
tools/re2c/dfa.h:63: error: syntax error before ‘:’ token
tools/re2c/dfa.h:65: error: syntax error before ‘*’ token
tools/re2c/dfa.h:65: warning: data definition has no type or storage class
tools/re2c/dfa.h:66: error: syntax error before ‘}’ token
tools/re2c/dfa.h:66: warning: data definition has no type or storage class
tools/re2c/dfa.h:68: error: syntax error before ‘State’
tools/re2c/dfa.h:69: error: syntax error before ‘State’
tools/re2c/dfa.h:70: error: syntax error before ‘State’
tools/re2c/dfa.h:71: error: syntax error before ‘State’
tools/re2c/dfa.h:72: error: syntax error before ‘State’
tools/re2c/dfa.h:74: error: syntax error before ‘State’
tools/re2c/dfa.h:76: error: syntax error before ‘*’ token
tools/re2c/dfa.h:76: warning: data definition has no type or storage class
tools/re2c/dfa.h:77: error: syntax error before ‘*’ token
tools/re2c/dfa.h:78: error: syntax error before ‘*’ token
tools/re2c/dfa.h:79: error: syntax error before ‘*’ token
tools/re2c/dfa.h:85: error: syntax error before ‘State’
tools/re2c/dfa.h:85: warning: no semicolon at end of struct or union
tools/re2c/dfa.h:86: warning: data definition has no type or storage class
tools/re2c/dfa.h:87: error: syntax error before ‘}’ token
tools/re2c/dfa.h:87: warning: data definition has no type or storage class
tools/re2c/dfa.h:89: error: syntax error before ‘*’ token
tools/re2c/dfa.h:89: error: syntax error before ‘*’ token
tools/re2c/dfa.h:89: warning: data definition has no type or storage class
tools/re2c/dfa.h:90: error: syntax error before ‘*’ token
tools/re2c/dfa.h:91: error: syntax error before ‘*’ token
tools/re2c/dfa.h:92: error: syntax error before ‘*’ token
tools/re2c/dfa.h:92: error: syntax error before ‘*’ token
tools/re2c/dfa.h:92: warning: data definition has no type or storage class
tools/re2c/dfa.h:93: error: syntax error before ‘*’ token
tools/re2c/dfa.h:95: error: syntax error before ‘*’ token
tools/re2c/dfa.h:96: error: syntax error before ‘*’ token
tools/re2c/dfa.h:97: error: syntax error before ‘*’ token
tools/re2c/dfa.h:99: error: syntax error before ‘*’ token
tools/re2c/dfa.h:100: error: syntax error before ‘*’ token
tools/re2c/dfa.h: In function ‘Action_new_Match’:
tools/re2c/dfa.h:102: error: ‘a’ undeclared (first use in this function)
tools/re2c/dfa.h:104: error: ‘s’ undeclared (first use in this function)
tools/re2c/dfa.h: At top level:
tools/re2c/dfa.h:109: error: syntax error before ‘*’ token
tools/re2c/dfa.h:110: error: syntax error before ‘*’ token
tools/re2c/dfa.h: In function ‘Action_new_Enter’:
tools/re2c/dfa.h:112: error: ‘a’ undeclared (first use in this function)
tools/re2c/dfa.h:114: error: ‘s’ undeclared (first use in this function)
tools/re2c/dfa.h:115: error: ‘l’ undeclared (first use in this function)
tools/re2c/dfa.h: At top level:
tools/re2c/dfa.h:120: error: syntax error before ‘*’ token
tools/re2c/dfa.h:121: error: syntax error before ‘*’ token
tools/re2c/dfa.h: In function ‘Action_new_Save’:
tools/re2c/dfa.h:123: error: ‘a’ undeclared (first use in this function)
tools/re2c/dfa.h:125: error: ‘s’ undeclared (first use in this function)
tools/re2c/dfa.h:126: error: ‘i’ undeclared (first use in this function)
tools/re2c/dfa.h: At top level:
tools/re2c/dfa.h:131: error: syntax error before ‘*’ token
tools/re2c/dfa.h:132: error: syntax error before ‘*’ token
tools/re2c/dfa.h: In function ‘Action_new_Move’:
tools/re2c/dfa.h:134: error: ‘a’ undeclared (first use in this function)
tools/re2c/dfa.h:136: error: ‘s’ undeclared (first use in this function)
tools/re2c/dfa.h: At top level:
tools/re2c/dfa.h:141: error: syntax error before ‘*’ token
tools/re2c/dfa.h:141: error: syntax error before ‘*’ token
tools/re2c/dfa.h:141: warning: data definition has no type or storage class
tools/re2c/dfa.h:143: error: syntax error before ‘*’ token
tools/re2c/dfa.h:144: error: syntax error before ‘*’ token
tools/re2c/dfa.h: In function ‘Action_new_Rule’:
tools/re2c/dfa.h:146: error: ‘a’ undeclared (first use in this function)
tools/re2c/dfa.h:148: error: ‘s’ undeclared (first use in this function)
tools/re2c/dfa.h:149: error: ‘r’ undeclared (first use in this function)
tools/re2c/dfa.h: At top level:
tools/re2c/dfa.h:155: error: syntax error before ‘*’ token
tools/re2c/dfa.h: In function ‘Action_isRule’:
tools/re2c/dfa.h:157: error: ‘a’ undeclared (first use in this function)
tools/re2c/dfa.h: At top level:
tools/re2c/dfa.h:161: error: syntax error before ‘*’ token
tools/re2c/dfa.h: In function ‘Action_isMatch’:
tools/re2c/dfa.h:163: error: ‘a’ undeclared (first use in this function)
tools/re2c/dfa.h: At top level:
tools/re2c/dfa.h:167: error: syntax error before ‘*’ token
tools/re2c/dfa.h: In function ‘Action_readAhead’:
tools/re2c/dfa.h:169: error: ‘a’ undeclared (first use in this function)
tools/re2c/main.c: In function ‘mystrdup’:
tools/re2c/main.c:77: warning: incompatible implicit declaration of built-in function ‘strlen’
tools/re2c/main.c:79: warning: incompatible implicit declaration of built-in function ‘memcpy’
tools/re2c/main.c: In function ‘main’:
tools/re2c/main.c:121: error: syntax error before ‘PACKAGE_VERSION’
tools/re2c/main.c:125: error: ‘PACKAGE_VERSION’ undeclared (first use in this function)
tools/re2c/main.c:175: warning: incompatible implicit declaration of built-in function ‘strlen’
make: *** [re2c-main.o] Error 1

```

Predictably, scanner.h, basics.h, and re.h are all where they are supposed to be. Any suggestions would be appreciated, the important thing being cinelerra rather than yasm.

Thanks.

---

