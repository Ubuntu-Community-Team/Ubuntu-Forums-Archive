---
title: "GTK+ Compiler Errors &quot;Undefined reference&quot;"
date: 2009-05-18
forum: General Help
---

### Post by MagPie&gt;.&lt; on 2009-05-18
I have recently started looking at GTK+ development for an application I am working on. I have apt-get'd all of the packages and gone through checking some others, but I am still getting problems at compile time:

```
gcc -Wall -g gtkt1.c -o gtkt1 `pkg-config --cflags --libs gtk+-2.0`
gtkt1.c: In function ‘main’:
gtkt1.c:32: warning: implicit declaration of function ‘gtk_set_window_title’
gtkt1.c:34: warning: implicit declaration of function ‘gtk_container_set_width’
/tmp/ccA1EvM1.o: In function `main':
/gtkt1.c:32: undefined reference to `gtk_set_window_title'
/gtkt1.c:34: undefined reference to `gtk_container_set_width'
collect2: ld returned 1 exit status

```

This is running GCC 4.3.2 and GTK+ 2.10.0 as far as I can tell, and I'm running Intrepid x86. Google had some errors from about two years ago, and I have done everything that was suggested by those posts, including on here, but to no avail.

Any help would be greatly appreciated :)

Nick

---

