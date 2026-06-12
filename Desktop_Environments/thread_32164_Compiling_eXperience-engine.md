---
title: "Compiling eXperience-engine"
date: 2005-05-06
forum: Desktop Environments
---

### Post by cannibalbob on 2005-05-06
I dled the gtk2-eXperience engine from art.gnome.org, installed byacc, and ran ./configure and make... it returned:
> Making all in src
make[1]: Entering directory `/home/andrew/experience-0.9.4.1.tar.bz2_FILES/experience-0.9.4.1/src'
yacc  -p experience_yy `test -f 'parser.y' || echo './'`parser.y
yacc: e - line 22 of "parser.y", syntax error
%pure_parser
^
make[1]: *** [parser.c] Error 1
make[1]: Leaving directory `/home/andrew/experience-0.9.4.1.tar.bz2_FILES/experience-0.9.4.1/src'
make: *** [all-recursive] Error 1

Any ideas? thanks.

---

### Post by Ptero-4 on 2005-05-08
[QUOTE=cannibalbob]I dled the gtk2-eXperience engine from art.gnome.org, installed byacc, and ran ./configure and make... it returned:


Any ideas? thanks.[/QUOTE]
 Contant the developper, from what I see there's an obvious synatx error in the line 22 of the parser.y file.  If you can post the contents of the parser.y file.

---

### Post by qball on 2005-05-08
install bison..

---

