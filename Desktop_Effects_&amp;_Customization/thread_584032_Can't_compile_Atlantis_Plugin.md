---
title: "Can't compile Atlantis Plugin"
date: 2007-10-20
forum: Desktop Effects &amp; Customization
---

### Post by Espreon on 2007-10-20
OK, I love the Atlantis,Snow and 3D plugins, But I can't compile them, this is the error messages like these when I try to compile them:

```

spanek@spanek-laptop:~/atlantis$ make
convert   : atlantis.xml.in -> build/atlantis.xml
bcop'ing  : build/atlantis.xml -> build/atlantis_options.h
bcop'ing  : build/atlantis.xml -> build/atlantis_options.c
schema'ing: build/atlantis.xml -> build/compiz-atlantis.schemawarning: failed to load external entity "/schemas.xslt"
cannot parse /schemas.xslt
make: *** [build/compiz-atlantis.schema] Error 4

```

Any suggestions?!?

---

### Post by Espreon on 2007-10-20
Bump.

---

### Post by Espreon on 2007-10-21
Come on people...

---

### Post by Khuezy on 2007-10-22
how did you get snow? I only have 3d window

---

### Post by Espreon on 2007-10-23
I got them from the GIT Repository....

BUT PEOPLE COME ON! I AM BEGGING YOU FOR HELP!
I could compile them on Sabayon.... but not Ubuntu...

---

### Post by err_ok on 2007-11-13
simple answer, use the Git4CF Automator(search for it on the forums) and uninstall the repo version of Compiz it's out of date. Then reinstall using that script. They will then compile perfectly.

---

### Post by maxfact on 2007-11-21
i have one problem when compile plugin atlantis:
```
 sudo make
[sudo] password for max:
compiling : atlantis.c -> build/atlantis.loIn file included from atlantis.c:108:
atlantis-internal.h:88:25: error: compiz-core.h: No such file or directory
atlantis-internal.h:89:25: error: compiz-cube.h: No such file or directory
In file included from atlantis.c:108:
atlantis-internal.h:113: error: expected specifier-qualifier-list before 'DonePaintScreenProc'
In file included from atlantis.c:109:
build/atlantis_options.h:23: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/atlantis_options.h:30: error: expected ')' before '*' token
build/atlantis_options.h:32: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/atlantis_options.h:45: error: expected ')' before '*' token
build/atlantis_options.h:47: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token

build/atlantis_options.h:49: error: expected ')' before '*' token
build/atlantis_options.h:50: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/atlantis_options.h:51: error: expected ')' before '*' token
build/atlantis_options.h:53: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'atlantisGetColors'
build/atlantis_options.h:54: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/atlantis_options.h:55: error: expected ')' before '*' token
build/atlantis_options.h:57: error: expected ')' before '*' token
build/atlantis_options.h:58: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/atlantis_options.h:59: error: expected ')' before '*' token
build/atlantis_options.h:61: error: expected ')' before '*' token
build/atlantis_options.h:62: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/atlantis_options.h:63: error: expected ')' before '*' token
build/atlantis_options.h:65: error: expected ')' before '*' token
build/atlantis_options.h:66: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/atlantis_options.h:67: error: expected ')' before '*' token
build/atlantis_options.h:69: error: expected ')' before '*' token
build/atlantis_options.h:70: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
build/atlantis_options.h:71: error: expected ')' before '*' token
atlantis.c:135: error: expected ')' before '*' token
atlantis.c:220: error: expected ')' before '*' token
atlantis.c:231: error: expected ')' before '*' token
atlantis.c:238: error: expected ')' before '*' token
atlantis.c:246: error: expected ')' before '*' token
atlantis.c:260: error: expected ')' before '*' token
atlantis.c:394: error: expected ')' before '*' token
atlantis.c:413: error: expected ')' before '*' token
atlantis.c:430: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'atlantisInitDisplay'
atlantis.c:461: error: expected ')' before '*' token
atlantis.c:471: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'atlantisInitScreen'
atlantis.c:513: error: expected ')' before '*' token
atlantis.c:530: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'atlantisInit'
atlantis.c:541: error: expected ')' before '*' token
atlantis.c:548: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'atlantisInitObject'
atlantis.c:561: error: expected ')' before '*' token
atlantis.c:573: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'atlantisVTable'
atlantis.c:585: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token

```

Why ask me file:

atlantis-internal.h:88:25: error: compiz-core.h: No such file or directory
atlantis-internal.h:89:25: error: compiz-cube.h: No such file or directory

compiz-core is installed 

i use ubuntu gutsy and i have compile plugin 3d is ok



Excuse for my english is very very bad :-\"

---

### Post by mrmiserable on 2007-11-22
try this and it has many more plugins enjoy photowheel

[http://forum.compiz-fusion.org/showthread.php?t=5303](http://forum.compiz-fusion.org/showthread.php?t=5303)

---

