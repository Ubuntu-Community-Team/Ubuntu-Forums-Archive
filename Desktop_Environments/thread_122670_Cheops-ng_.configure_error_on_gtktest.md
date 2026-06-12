---
title: "Cheops-ng ./configure error on gtktest"
date: 2006-01-28
forum: Desktop Environments
---

### Post by Luke771 on 2006-01-28
I'm having a hard time trying to install Cheops-ng.
I have downloaded the .tgz file from Sourceforge, then uncompressed it running```

tar -zxvf cheops-ng-0.2.3.tgz 
```
Then I should run ```
./configure
```
But when I do, I keep getting an error on gtktest:> 
checking for gtk-config... (cached) /usr/bin/gtk-config
checking for GTK - version >= 1.2.0... no
*** Could not run GTK test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GTK was incorrectly installed
*** or that you have moved GTK since it was installed. In the latter case, you
*** may want to edit the gtk-config script: /usr/bin/gtk-config
configure: error: Cannot find GTK: Is gtk-config in path

Then I looked at config.log; when some kind ok gtk is first seen, the file goes on like this:
> 
configure:3396: checking for gtk-config
configure:3431: checking for GTK - version >= 1.2.0
configure:3532: gcc -o conftest -g -O2 -Wall  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include   conftest.c -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lnsl -lpthread -lncurses -lpthread 1>&5
configure:3635: checking for SmcSaveYourselfDone in -lSM
configure:3654: gcc -o conftest -g -O2 -Wall   -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include  -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm conftest.c -lSM  -lICE -lnsl -lpthread -lncurses -lpthread 1>&5
configure:3683: checking for X11/SM/SMlib.h
configure:3693: gcc -E  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include conftest.c >/dev/null 2>conftest.out
configure:3731: checking for XpmFreeXpmImage in -lXpm
configure:3750: gcc -o conftest -g -O2 -Wall   -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include  -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm conftest.c -lXpm  -lnsl -lpthread -lncurses -lpthread 1>&5
configure:3830: checking for gtk-config
configure:3865: checking for GTK - version >= 1.2.0
configure:3966: gcc -o conftest -g -O2 -Wall  -I/usr/include/gnome-1.0 -DNEED_GNOMESUPPORT_H -I/usr/lib/gnome-libs/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include  conftest.c -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lnsl -lpthread -lncurses -lpthread -lSM -lICE -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -L/usr/lib  -lgnomeui -lart_lgpl -L/usr/lib -lgdk_imlib -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lSM -lICE -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lgnome -lgnomesupport -L/usr/lib -lesd -laudiofile -lm -L/usr/lib -laudiofile -lm -ldb-3 -L/usr/lib -lglib  1>&5
/usr/bin/ld: cannot find -lgnomeui
collect2: ld returned 1 exit status
configure: failed program was:
#line 3888 "configure"
#include "confdefs.h"

#include <gtk/gtk.h>
#include <stdio.h>
#include <stdlib.h>

int 
main ()
{
  int major, minor, micro;
  char *tmp_version;

  system ("touch conf.gtktest");

  /* HP/UX 9 (%@#!) writes to sscanf strings */
  tmp_version = g_strdup("1.2.0");
  if (sscanf(tmp_version, "%d.%d.%d", &major, &minor, &micro) != 3) {
     printf("%s, bad version string\n", "1.2.0");
     exit(1);
   }

  if ((gtk_major_version != 1) ||
      (gtk_minor_version != 2) ||
      (gtk_micro_version != 10))
    {
      printf("\n*** 'gtk-config --version' returned %d.%d.%d, but GTK+ (%d.%d.%d)\n", 
             1, 2, 10,
             gtk_major_version, gtk_minor_version, gtk_micro_version);
      printf ("*** was found! If gtk-config was correct, then it is best\n");
      printf ("*** to remove the old version of GTK+. You may also be able to fix the error\n");
      printf("*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing\n");
      printf("*** /etc/ld.so.conf. Make sure you have run ldconfig if that is\n");
      printf("*** required on your system.\n");
      printf("*** If gtk-config was wrong, set the environment variable GTK_CONFIG\n");
      printf("*** to point to the correct copy of gtk-config, and remove the file config.cache\n");
      printf("*** before re-running configure\n");
    } 
#if defined (GTK_MAJOR_VERSION) && defined (GTK_MINOR_VERSION) && defined (GTK_MICRO_VERSION)
  else if ((gtk_major_version != GTK_MAJOR_VERSION) ||
	   (gtk_minor_version != GTK_MINOR_VERSION) ||
           (gtk_micro_version != GTK_MICRO_VERSION))
    {
      printf("*** GTK+ header files (version %d.%d.%d) do not match\n",
	     GTK_MAJOR_VERSION, GTK_MINOR_VERSION, GTK_MICRO_VERSION);
      printf("*** library (version %d.%d.%d)\n",
	     gtk_major_version, gtk_minor_version, gtk_micro_version);
    }
#endif /* defined (GTK_MAJOR_VERSION) ... */
  else
    {
      if ((gtk_major_version > major) ||
        ((gtk_major_version == major) && (gtk_minor_version > minor)) ||
        ((gtk_major_version == major) && (gtk_minor_version == minor) && (gtk_micro_version >= micro)))
      {
        return 0;
       }
     else
      {
        printf("\n*** An old version of GTK+ (%d.%d.%d) was found.\n",
               gtk_major_version, gtk_minor_version, gtk_micro_version);
        printf("*** You need a version of GTK+ newer than %d.%d.%d. The latest version of\n",
	       major, minor, micro);
        printf("*** GTK+ is always available from ftp://ftp.gtk.org.\n");
        printf("***\n");
        printf("*** If you have already installed a sufficiently new version, this error\n");
        printf("*** probably means that the wrong copy of the gtk-config shell script is\n");
        printf("*** being found. The easiest way to fix this is to remove the old version\n");
        printf("*** of GTK+, but you can also set the GTK_CONFIG environment to point to the\n");
        printf("*** correct copy of gtk-config. (In this case, you will have to\n");
        printf("*** modify your LD_LIBRARY_PATH enviroment variable, or edit /etc/ld.so.conf\n");
        printf("*** so that the correct libraries are found at run-time))\n");
      }
    }
  return 1;
}

configure:4010: gcc -o conftest -g -O2 -Wall  -I/usr/include/gnome-1.0 -DNEED_GNOMESUPPORT_H -I/usr/lib/gnome-libs/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include  -I/usr/include/gtk-1.2 -I/usr/include/glib-1.2 -I/usr/lib/glib/include -I/usr/X11R6/include  conftest.c -lnsl -lpthread -lncurses -lpthread -lSM -lICE -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -L/usr/lib  -lgnomeui -lart_lgpl -L/usr/lib -lgdk_imlib -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lSM -lICE -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm -lgnome -lgnomesupport -L/usr/lib -lesd -laudiofile -lm -L/usr/lib -laudiofile -lm -ldb-3 -L/usr/lib -lglib  -L/usr/lib -L/usr/X11R6/lib -lgtk -lgdk -rdynamic -lgmodule -lglib -ldl -lXi -lXext -lX11 -lm 1>&5
/usr/bin/ld: cannot find -lgnomeui
collect2: ld returned 1 exit status
configure: failed program was:
#line 4000 "configure"
#include "confdefs.h"

#include <gtk/gtk.h>
#include <stdio.h>

int main() {
 return ((gtk_major_version) || (gtk_minor_version) || (gtk_micro_version)); 
; return 0; }


...please help?

---

### Post by cwaldbieser on 2006-01-28
This line is the culprit:
```

/usr/bin/ld: cannot find -lgnomeui

```
It needs to link against the libgnomeui library, but it can't find it.

---

