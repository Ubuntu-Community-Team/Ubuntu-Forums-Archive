---
title: "how can i send to msg to all my buddies in GAIM (like send t o all in ym?) ?"
date: 2006-10-23
forum: Desktop Environments
---

### Post by Nurazri on 2006-10-23
really hope someone can help me here.
how can i send message to all my buddies in GAIM ? more like YM send to all function. 

thanks in advance

---

### Post by gnudownload on 2006-11-01
yes
you can use "Send To Some"
[http://www.cse.iitb.ac.in/~dineshg/files/plugin/gaim-plugin-send-some/](http://www.cse.iitb.ac.in/~dineshg/files/plugin/gaim-plugin-send-some/)

---

### Post by Nurazri on 2006-11-04
thanks for the list

i tried compiling the sendsome.c, but it doesn't work

make sendsome.so
/bin/sh ../libtool --silent --mode=compile gcc -DHAVE_CONFIG_H -I.. -DDATADIR=\" /usr/local/share\" -DVERSION=\"1.5.0\" -I../src  -I/usr/include/gtk-2.0 -I/usr/l ib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/pa ngo-1.0 -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include    -g -O2 -Wall -g3 -c sendsome.c -o tmpsendsome.so.lo
sendsome.c: In function 'send_all_cb':
sendsome.c:212: error: invalid lvalue in assignment
sendsome.c:216: error: invalid lvalue in assignment
make: *** [sendsome.so] Error 1

any ideas please?

thanks a lot for the link tho. at least i have somewhere to start with

---

