---
title: "how do i make an error not appear?"
date: 2009-04-07
forum: General Help
---

### Post by chriskin on 2009-04-07
every time i use the sudo command and a program opens, i get this error

> /root/.themes/Dust Mac/gtk-2.0/gtkrc:77: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/root/.themes/Dust Mac/gtk-2.0/gtkrc:78: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/root/.themes/Dust Mac/gtk-2.0/gtkrc:93: Murrine configuration option "style" is not supported and will be ignored.
/root/.themes/Dust Mac/gtk-2.0/gtkrc:172: Murrine configuration option "style" is not supported and will be ignored.
/root/.themes/Dust Mac/gtk-2.0/gtkrc:202: Murrine configuration option "style" is not supported and will be ignored.
/root/.themes/Dust Mac/gtk-2.0/gtkrc:310: Murrine configuration option "style" is not supported and will be ignored.
/root/.themes/Dust Mac/gtk-2.0/gtkrc:344: Murrine configuration option "style" is not supported and will be ignored.


it doesn't seem to cause any problem,  how can i make it not appear?

:popcorn:

---

### Post by zacktu on 2009-04-07
If you're asking how to avoid seeing messages sent to stderr, you can redirect them to /dev/null.  For example,

sudo mycommand 2> /dev/null

will make error messages not appear.  You will still see messages sent to stdout.

---

### Post by chriskin on 2009-04-07
> **zacktu said:**
> If you're asking how to avoid seeing messages sent to stderr, you can redirect them to /dev/null.  For example,

sudo mycommand 2> /dev/null

will make error messages not appear.  You will still see messages sent to stdout.


won't this be temporary?
i can't write 2> /dev/null all the time , i prefer seeing a pointless error about my finely working dust mac theme, and it won't be only about these errors but all of them, or so i understood. 

isn't there a way to make this specific error disappear?

---

