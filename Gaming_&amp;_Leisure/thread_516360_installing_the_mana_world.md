---
title: "installing the mana world"
date: 2007-08-03
forum: Gaming &amp; Leisure
---

### Post by Luksion Knight on 2007-08-03
hey im having a problem with the "make" command in src. it gives the return ```
g++ -DHAVE_CONFIG_H -I. -I..  -DTMW_DATADIR=\""/usr/local/share/tmw/"\"   -Wall -DUSE_OPENGL -I/usr/include/SDL -D_GNU_SOURCE=1 -D_REENTRANT `pkg-config --cflags libxml-2.0`  -g -O2 -MT tmw-browserbox.o -MD -MP -MF .deps/tmw-browserbox.Tpo -c -o tmw-browserbox.o `test -f 'gui/browserbox.cpp' || echo './'`gui/browserbox.cpp
gui/browserbox.h:93: error: ‘gcn::MouseEvent’ has not been declared
gui/browserbox.h:94: error: ‘gcn::MouseEvent’ has not been declared
gui/browserbox.cpp:242: error: variable or field ‘mousePressed’ declared void
gui/browserbox.cpp:242: error: ‘int BrowserBox::mousePressed’ is not a static member of ‘class BrowserBox’
gui/browserbox.cpp:242: error: ‘MouseEvent’ is not a member of ‘gcn’
gui/browserbox.cpp:242: error: ‘event’ was not declared in this scope
gui/browserbox.cpp:243: error: expected ‘,’ or ‘;’ before ‘{’ token
gui/browserbox.cpp:253: error: variable or field ‘mouseMoved’ declared void
gui/browserbox.cpp:253: error: ‘int BrowserBox::mouseMoved’ is not a static member of ‘class BrowserBox’
gui/browserbox.cpp:253: error: ‘MouseEvent’ is not a member of ‘gcn’
gui/browserbox.cpp:253: error: ‘event’ was not declared in this scope
gui/browserbox.cpp:254: error: expected ‘,’ or ‘;’ before ‘{’ token
make: *** [tmw-browserbox.o] Error 1

```

any help?

---

