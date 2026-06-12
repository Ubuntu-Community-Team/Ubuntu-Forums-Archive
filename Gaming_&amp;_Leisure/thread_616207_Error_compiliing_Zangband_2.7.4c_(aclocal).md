---
title: "Error compiliing Zangband 2.7.4c (aclocal)"
date: 2007-11-18
forum: Gaming &amp; Leisure
---

### Post by gcrussell1 on 2007-11-18
I have build-essential installed, and I've compiled a number of apps already and overcome issues with most of them as well. I'm trying to compile Zangband 2.7.4c and the configure works fine, but when I run make I get this```
greg@greg-laptop:~/Desktop/zangband$ sudo make
aclocal
make: aclocal: Command not found
make: *** [configure] Error 127
```I've checked a couple threads with aclocal problems, and it seems that some of them were fixed by creating a symbolic "aclocal" link to "aclocal1.9" and stuff like that - the problem is that I have nothing regarding aclocal in my /usr/bin like they mentioned - a quick search of the file system finds a folder named aclocal in the /usr/share directory and a doc named aclocal.h in the /usr/src/linux-headers-2.6.22-14/include/acpi directory. Note that the latest source for Zangband is over 3 1/2 years old, so that might have something to do with it.

Any help?

---

### Post by Pdavid on 2007-11-18
I had some luck a while ago with "sudo apt-get build-dep zangband", though I think I was compiling a different version.

Also, there's 2.7.5 beta or something on the sourceforge page. I haven't played either much, but I think the 2.7.5 one is meant to be more stable.

[http://sourceforge.net/project/showfiles.php?group_id=11392]("http://sourceforge.net/project/showfiles.php?group_id=11392")


edit: it seems you need the package "automake" (sudo apt-get install automake), but I still couldn't successfully build it. Got this output:
```

In file included from /usr/include/gtk-1.2/gdk/gdktypes.h:33,
                 from /usr/include/gtk-1.2/gdk/gdk.h:31,
                 from /usr/include/gtk-1.2/gtk/gtk.h:31,
                 from main-gtk.c:47:
/usr/include/glib-1.2/glib.h:1308:23: warning: ISO C does not permit named variadic macros
/usr/include/glib-1.2/glib.h:1311:25: warning: ISO C does not permit named variadic macros
/usr/include/glib-1.2/glib.h:1314:26: warning: ISO C does not permit named variadic macros
/usr/include/glib-1.2/glib.h:1317:25: warning: ISO C does not permit named variadic macros
In file included from /usr/include/gtk-1.2/gtk/gtkarg.h:31,
                 from /usr/include/gtk-1.2/gtk/gtkobject.h:31,
                 from /usr/include/gtk-1.2/gtk/gtkaccelgroup.h:35,
                 from /usr/include/gtk-1.2/gtk/gtk.h:32,
                 from main-gtk.c:47:
/usr/include/gtk-1.2/gtk/gtktypeutils.h:163: warning: function declaration isn&#8217;t a prototype
In file included from /usr/include/gtk-1.2/gtk/gtk.h:80,
                 from main-gtk.c:47:
/usr/include/gtk-1.2/gtk/gtkitemfactory.h:48: warning: function declaration isn&#8217;t a prototype
main-gtk.c: In function &#8216;change_graf_mode_event_handler&#8217;:
main-gtk.c:1615: warning: cast from pointer to integer of different size
main-gtk.c:1618: warning: cast from pointer to integer of different size
main-gtk.c: At top level:
main-gtk.c:2332: error: initialiser element is not constant
main-gtk.c:2332: error: (near initialisation for &#8216;main_menu_items[7].callback_action&#8217;)
main-gtk.c:2334: error: initialiser element is not constant
main-gtk.c:2334: error: (near initialisation for &#8216;main_menu_items[8].callback_action&#8217;)
main-gtk.c:2336: error: initialiser element is not constant
main-gtk.c:2336: error: (near initialisation for &#8216;main_menu_items[9].callback_action&#8217;)
main-gtk.c:2338: error: initialiser element is not constant
main-gtk.c:2338: error: (near initialisation for &#8216;main_menu_items[10].callback_action&#8217;)
main-gtk.c:2340: error: initialiser element is not constant
main-gtk.c:2340: error: (near initialisation for &#8216;main_menu_items[11].callback_action&#8217;)
main-gtk.c:2342: error: initialiser element is not constant
main-gtk.c:2342: error: (near initialisation for &#8216;main_menu_items[12].callback_action&#8217;)
main-gtk.c:2344: error: initialiser element is not constant
main-gtk.c:2344: error: (near initialisation for &#8216;main_menu_items[13].callback_action&#8217;)
main-gtk.c:2346: error: initialiser element is not constant
main-gtk.c:2346: error: (near initialisation for &#8216;main_menu_items[14].callback_action&#8217;)
main-gtk.c:2357: error: initialiser element is not constant
main-gtk.c:2357: error: (near initialisation for &#8216;main_menu_items[17].callback_action&#8217;)
main-gtk.c:2359: error: initialiser element is not constant
main-gtk.c:2359: error: (near initialisation for &#8216;main_menu_items[18].callback_action&#8217;)
main-gtk.c:2361: error: initialiser element is not constant
main-gtk.c:2361: error: (near initialisation for &#8216;main_menu_items[19].callback_action&#8217;)
main-gtk.c:2363: error: initialiser element is not constant
main-gtk.c:2363: error: (near initialisation for &#8216;main_menu_items[20].callback_action&#8217;)
main-gtk.c:2365: error: initialiser element is not constant
main-gtk.c:2365: error: (near initialisation for &#8216;main_menu_items[21].callback_action&#8217;)
main-gtk.c:2367: error: initialiser element is not constant
main-gtk.c:2367: error: (near initialisation for &#8216;main_menu_items[22].callback_action&#8217;)
main-gtk.c:2369: error: initialiser element is not constant
main-gtk.c:2369: error: (near initialisation for &#8216;main_menu_items[23].callback_action&#8217;)
main-gtk.c:2371: error: initialiser element is not constant
main-gtk.c:2371: error: (near initialisation for &#8216;main_menu_items[24].callback_action&#8217;)
make: *** [main-gtk.o] Error 1

```

(I'm guessing that I'm missing dependencies of some description)

I went into the src directory and edited "makefile.std" (for example, "vi makefile.std") so the line that said ```
DEFAULT := linux
```
now sayd
```
DEFAULT := linux-no-gtk
```

and ran ```
make -f makefile.std
```

and that seemed to work, though pushing * at character creation seems to crash the game.

---

### Post by gcrussell1 on 2007-11-18
Much appreciated - I'm currently running my XP partition for some proprietary stuff, but I'll be sure to try all that when I jump back to Ubuntu (hopefully sooner rather than later... I hate being in Windows these days).

EDIT: No luck - with the build-dep stuff I was able to compile Zangband, but GTK won't run it (something about elevated privileges not being allowed). I tried the other change you mentioned, the no-gtk thing, and it works on the make, but then comes out at the end of pages and pages of output (fills up the terminal's max line count and then some) and says there's one error and aborts. No mention of what the error is though.

I think I'm just gonna give up... I didn't really want to play Zangband that badly anyway - I downloaded it while I was bored and thought I'd see how it compared to Vanilla, but then, I don't have too much time to be bored anyway, so it's probably best not to have a roguelike on my computer as those things eat time for breakfast, lunch, and dinner.

---

### Post by Beren Camlost on 2007-11-20
Another old classic from the Amiga days! :guitar:

I haven't compiled Zangband on Linux myself, but I found some notes on which versions have been succesfully compiled on various platforms [here]("http://www.thangorodrim.net/zangband.html").

As I don't know what is the difference between Zangband and the original Angband, I suggest you can try with the original Angband. It goes through active developement still and I have succesfully compiled it on Kubuntu Feisty without problems. A short walkthrough can be found [here]("http://www.thangorodrim.net/compiling.html#Linux_GCC"), but it's adviced to use the latest source from the [official site]("http://rephial.org/").

---

