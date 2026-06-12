---
title: "Having problem running Lordsawar - ubuntu 8.10"
date: 2009-04-18
forum: Gaming &amp; Leisure
---

### Post by SwordsmanJ on 2009-04-18
I installed the game from the Add/remove programs menu under applications. I can get the load screen, where you select new game, load game, load scenario, preferences, etc. When I hit new game, program crashes. This is what my system log says (under messages, syslog, and kern.log):
> Apr 18 15:34:45 j-ulap kernel: [ 8610.430817] lordsawar[19984]: segfault at 13c ip b7f3d443 sp bfe21700 error 4 in libSDL-1.2.so.0.11.1[b7f0c000+67000]

I followed the directions from here, downloading the tar etc: [http://gaming.gwos.org/doku.php/guides:64bit:lordsawar?s=lordsawar](http://gaming.gwos.org/doku.php/guides:64bit:lordsawar?s=lordsawar)
Everything was fine, til I get to the "./configure" step, it told me intltools was out of date.

Had to update intltools, which i did from here: [http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html](http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html)

Now, when I run "./configure", it tells me: > configure: error: GNU gettext tools not found; required for intltool. tried installing that with tar from here: [http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/)
End up with these errors during install:
> chmod: changing permissions of `/usr/local/lib/libasprintf.a': Operation not permitted
make[3]: *** [install-libLTLIBRARIES] Error 1
make[3]: Leaving directory `/home/jared/Desktop/gettext-0.17/gettext-runtime/libasprintf'
make[2]: *** [install-am] Error 2
make[2]: Leaving directory `/home/jared/Desktop/gettext-0.17/gettext-runtime/libasprintf'
make[1]: *** [install-recursive] Error 1
make[1]: Leaving directory `/home/jared/Desktop/gettext-0.17/gettext-runtime'
make: *** [install-recursive] Error 1

****  Installation failed. Aborting package creation.

And this is where I'm stuck. Any idea where I should go from here?

---

### Post by Grishka on 2009-04-18
> **SwordsmanJ said:**
> I installed the game from the Add/remove programs menu under applications. I can get the load screen, where you select new game, load game, load scenario, preferences, etc. When I hit new game, program crashes. This is what my system log says (under messages, syslog, and kern.log):


I followed the directions from here, downloading the tar etc: [http://gaming.gwos.org/doku.php/guides:64bit:lordsawar?s=lordsawar](http://gaming.gwos.org/doku.php/guides:64bit:lordsawar?s=lordsawar)
Everything was fine, til I get to the "./configure" step, it told me intltools was out of date.

Had to update intltools, which i did from here: [http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html](http://www.linuxfromscratch.org/blfs/view/svn/general/intltool.html)

Now, when I run "./configure", it tells me: . tried installing that with tar from here: [http://www.gnu.org/software/gettext/](http://www.gnu.org/software/gettext/)
End up with these errors during install:


And this is where I'm stuck. Any idea where I should go from here?

ouch. you don't have to compile everything, you know. gettext is in the repos ([apt://gettext]("apt://gettext")). sdl libraries as well. ([apt://libsdl1.2-dev]("apt://libsdl1.2-dev")). as for lordsawar, if you won't manage to run the ubuntu version, try installing from svn. (svn://lordsawar.com/lordsawar/)

---

