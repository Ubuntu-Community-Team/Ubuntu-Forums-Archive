---
title: "prob compiling mangband"
date: 2007-05-12
forum: Gaming &amp; Leisure
---

### Post by richieboy on 2007-05-12
hi.

i posted this on the manband bb also.  trying to make in the src file i get this error:

  
gcc -Wall -g -pipe -D"USE_GCU" -I/usr/include/lncurses -o server/netserver.o -c server/netserver.c
server/netserver.c:101: error: static declaration of &#8216;Id&#8217; follows non-static declaration
server/externs.h:18: error: previous declaration of &#8216;Id&#8217; was here
server/netserver.c: In function &#8216;change_password&#8217;:
server/netserver.c:5107: warning: control reaches end of non-void function
make: *** [server/netserver.o] Error 1
 
can anyone tell me how to fix this, please?
 
thanks,
 
rich:confused: :(

---

