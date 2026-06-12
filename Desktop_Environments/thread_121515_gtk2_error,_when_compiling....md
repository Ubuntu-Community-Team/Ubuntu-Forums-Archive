---
title: "gtk2 error, when compiling..."
date: 2006-01-25
forum: Desktop Environments
---

### Post by DivadLarsen on 2006-01-25
Hello there,
after a quick search on the net, I can't seem to find any solution to my current problem.
I'm running Kubuntu 5.10, but as I tried compiling Gaim2 on my system, I got this message:

"checking for GLIB - version >= 2.0.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occurred. This usually means GLIB is incorrectly installed.
configure: error:
*** GLib 2.0 is required to build Gaim; please make sure you have the GLib
*** development headers installed. The latest version of GLib is
*** always available at http://www.gtk.org/."

Then, I've tried upgrading my gtk2 libs (apt-get installl gtk2.0-0). But that hasn't helped. Yet I tried downloading and installing from gtk.org (plus given dependecies) but it still doesn't work...
Anyone who can help me...?? Would be kinda nice, as I find it seriously annoying not being able to compile...

Thanks to paying attention..!!!

---

### Post by quux on 2006-01-25
try installing the gtk2.0-dev packages:

sudo apt-get install libgtk2.0-dev

---

### Post by DivadLarsen on 2006-01-25
hmmm... Well, tried the gtk2-dev package, but it didn't seem to change anything.. Still same annoying problem....

---

### Post by quux on 2006-01-25
Strange... 2.0.0beta2 compiles flawlessly here (using ubuntu breezy). Could you please tell me the output of:

pkg-config --list-all | grep -E "^(gtk|glib)"

---

### Post by DivadLarsen on 2006-01-25
root@vaerelset:/home/david/install/gaim-2.0.0beta2# pkg-config --list-all | grep -E "^(gtk|glib)"
glib-2.0              GLib - C Utility Library
glibmm-2.4            GLibmm - C++ wrapper for GLib
gtk+-2.0              GTK+ - GIMP Tool Kit (x11 target)
gtk+-x11-2.0          GTK+ - GIMP Tool Kit (x11 target)

That would be just about it.....

---

### Post by quux on 2006-01-25
Hmm... does the following program compile/run?

$ cat t.c
#include <glib.h>
#include <stdio.h>
int main() {
  printf("%d.%d.%d\n",
      glib_major_version,
      glib_minor_version,
      glib_micro_version);
  return 0;
}

$ gcc `pkg-config --cflags --libs glib-2.0` t.c && ./a.out

---

### Post by DivadLarsen on 2006-01-25
Sorry, I didn't quite catch that...

(it tried running "cat t.c" and "gcc `pkg-config --cflags --libs glib-2.0` t.c && ./a.out" as you requested, without any succes)

I am somewhat of a newbie when speaking of system setups...

---

### Post by DivadLarsen on 2006-01-25
This is the result I get, when inserting all you wrote:

root@vaerelset:/home/david#  cat t.c
cat: t.c: Ingen sådan fil eller filkatalog <- No such file or catalogue (Sorry, danish)
root@vaerelset:/home/david# #include <glib.h>
root@vaerelset:/home/david# #include <stdio.h>
root@vaerelset:/home/david# int main() {
bash: syntax error near unexpected token `('
root@vaerelset:/home/david# printf("%d.%d.%d\n",
bash: syntax error near unexpected token `"%d.%d.%d\n",'
root@vaerelset:/home/david# glib_major_version,
bash: glib_major_version,: command not found
root@vaerelset:/home/david# glib_minor_version,
bash: glib_minor_version,: command not found
root@vaerelset:/home/david# glib_micro_version);
bash: syntax error near unexpected token `)'
root@vaerelset:/home/david# return 0;
bash: return: can only `return' from a function or sourced script
root@vaerelset:/home/david# }
bash: syntax error near unexpected token `}'
root@vaerelset:/home/david#
root@vaerelset:/home/david# gcc `pkg-config --cflags --libs glib-2.0` t.c && ./a.out
gcc: t.c: Ingen sådan fil eller filkatalog <- No such file or catalogue (sorry again)

So I guess that isn't too possitive now, is it?? (hehe)

---

### Post by quux on 2006-01-25
Sorry for making myself not clear enough, what I really meant was: could you please put the lines ```

#include <glib.h>
#include <stdio.h>
int main() {
  printf("%d.%d.%d\n",
    glib_major_version,
    glib_minor_version,
    glib_micro_version);
  return 0;
}
``` in a file named "t.c" and then execute
```
gcc `pkg-config --cflags --libs glib-2.0` t.c && ./a.out
``` on the command line.

---

### Post by DivadLarsen on 2006-01-26
Hello again and sorry that I'm a bit late, but there was (apparently) a problem with our internet connection... (slow administrator, that is)..

Well.. When running the command, I get this message:

root@vaerelset:/home/david# gcc `pkg-config --cflags --libs glib-2.0` t.c && ./a.out
t.c:1:18: error: glib.h: Ingen sådan fil eller filkatalog <-(no such file.. you know the drill)
t.c: In function &#8216;main&#8217;:
t.c:5: fejl: &#8216;glib_major_version&#8217; undeclared (first use in this function)
t.c:5: fejl: (et kaldenavn der ikke er erklæret, rapporteres kun én gang
t.c:5: fejl: per funktion)
t.c:6: fejl: &#8216;glib_minor_version&#8217; undeclared (first use in this function)
t.c:7: fejl: &#8216;glib_micro_version&#8217; undeclared (first use in this function)

I'm truely sorry if I'm doing anything wrong, but I basically haven't got a clue of
what I'm dealing with here....

---

### Post by quux on 2006-01-26
.

---

### Post by quux on 2006-01-26
Judging from the error message only, i'd say that you are missing the package "libglib2.0-dev" which contains "/usr/include/glib-2.0/glib.h"... the file your compiler cannot find. 

Unfortunately your pkg-config output tells otherwise... :/

Maybe there's an alternative to compling the program yourself: if you just want to use the program you can try the packages on [http://mighmos.org/packages.php](http://mighmos.org/packages.php)

Just get the archive, untar and install via
```

sudo dpkg -i gaim_2.0.0-1beta2_i386.deb gaim-data_2.0.0-1beta2_all.deb gaim-dev_2.0.0-1beta2_i386.deb

```

---

### Post by DivadLarsen on 2006-01-27
hmm.. It seems I've already got the libglib2.0-dev package installed....

But anyway... Thanks for the advices and help..

---

