---
title: "GLib compile issue"
date: 2009-02-19
forum: General Help
---

### Post by ranthal on 2009-02-19
Hey all,

I'm working on a program right now that uses GLib for key-value files to configure the program.  When I try to compile it via a Makefile it cannot find the various GLib headers located in /usr/include/glib-2.0/glib/.  The snippet of code from the Makefile that shoud do it is:

%.o: %.c $(HEADERS)
    $(SUMMARY) "==> Compiling C $<"
    $(SUMMARY) $(INCLUDES)
    $(CC) $(CFLAGS) -c -I/usr/include/glib-2.0 $< -o $@

However when I run make all it drops the -I option so that in the console output it reads:

gcc -ggdb -fno-schedule-insns -fno-schedule-insns2   -c -o api-tool.o api-tool.c

And the header files are not found, doesn't compile, etc.  Any ideas why it is dropping the include?

---

### Post by ranthal on 2009-02-19
Got it.  Having the $(HEADERS) macro was screwing with the prerequisites so the execution of gcc was all screwy.

---

