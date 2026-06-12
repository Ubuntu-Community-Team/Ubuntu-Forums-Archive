---
title: "How to Compile Wubi?"
date: 2009-02-04
forum: General Help
---

### Post by fprg on 2009-02-04
Hi,I want to modify Wubi. When I run "make prerequisites"  and  "make" commands with the source code, I got a mistake below :

> DEBUG:translate:['./tools/translate', 'src/wubi/english.nsh', 'po/wubi.pot', 'po', 'build/translations', 'po/ignore.po']
DEBUG:translate:nsh2pot /home/fyh/Wubi/src/wubi/english.nsh -> /home/fyh/Wubi/po/wubi.pot
DEBUG:translate:Updating generated file.
bzr: ERROR: Not a branch: "/home/fyh/Wubi/".
Traceback (most recent call last):
File "./tools/translate", line 101, in <module>
update_all(*args)
File "./tools/translate", line 91, in update_all
nsh2pot(nshtemplate, potfile, poignore)
File "./tools/translate", line 60, in nsh2pot
text = text.replace('VERSION', str(bzr_revno()))
File "./tools/translate", line 37, in bzr_revno
return int(child_stdout.readline())
ValueError: invalid literal for int() with base 10: ''
make: *** [translations] ERROR 1

Is there anyone know What's Wrong? What's wrong with bzr?
Is there any articles explaining How to Compile Wubi?

---

### Post by ago on 2009-02-04
You are using the old version

bzr branch lp:wubi
cd wubi
make

---

