---
title: "xchat 2.6.0"
date: 2005-11-03
forum: Closed Requests
---

### Post by akurashy on 2005-11-03
The sources just when out today, i tried to compile it but i failed, not much of a compiler here :(

hoping to see it in ubuntu repository soon :)

---

### Post by vassie on 2005-11-03
I'd like to see this too

Ben

---

### Post by donar73 on 2005-11-03
*bump*

---

### Post by btdown on 2005-11-04
Yeah I'd like this too... I'm going to give it a shot at compiling, but I have a question. I already have the latest version of Xchat installed via synaptic. Do I need to uninstall it first before I compile the new version? What would happen if I didnt uninstall it and compiled/installed the new version?
Thanks
BT
 
 
Edit: Didnt compile for me...had a lot of errors...couldnt find python, couldnt find gtk or glib...who knows...this is insane.... I'll wait for some kind soul to pkg it up.

---

### Post by niko_ on 2005-11-04
hi, thanks for letting me know its out :)
I downloaded, extracted the source, put the patch, configured, compiled
after that i removed the old xchat (*sudo apt-get remove xchat*) and then *sudo make install* and it works without problems. Maybe i will write a howto if this is so serious. If you got some compilation errors, let me know, maybe i can help.

anyways i attached the screenshot for 'proof':

[ATTACH]3360[/ATTACH]

---

### Post by btdown on 2005-11-04
Ok.. I think I got all the deps installed by installing everything I thought looked vaguely appropriate for the errors it produced, and now it looks like ./configure works without a hitch giving me this:
> xchat 2.6.0
Building GTK+ Interface .... : yes
Building TEXT Interface .... : no
PLUGINS: Perl: yes Python: yes TCL: no DBUS: no
mmx tinting ......... : yes
XShm tinting ........ : no plugin interface .... : yes
text backend ........ : pango nls/gettext ......... : yes
openssl support ..... : no ipv6 support ........ : no
The binary will be installed in /usr/local/bin
configure complete, now type 'make' and pray.

 
When I do a make, it errors out:
> make[4]: Entering directory `/home/btdown/Desktop/xchat-2.6.0/plugins/perl'
/bin/sh ../../libtool --tag=CC --mode=link gcc -g -O2 -Wall -pipe -Wno-pointer-sign -funsigned-char -o perl.la -rpath /usr/local/lib/xchat/plugins -avoid-version -module perl.lo -Wl,-E -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -ldl -lm -lpthread -lcrypt -ldl -Wl,--export-dynamic -ldl -lglib-2.0
*** Warning: Linking the shared library perl.la against the
*** static library /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a is not portable!
gcc -shared .libs/perl.o -L/usr/local/lib /usr/lib/perl/5.8/auto/DynaLoader/DynaLoader.a -L/usr/lib/perl/5.8/CORE -lperl -lm -lpthread -lcrypt -ldl /usr/lib/libglib-2.0.so -Wl,-E -Wl,--export-dynamic -Wl,-soname -Wl,perl.so -o .libs/perl.so
/usr/bin/ld: cannot find -lperl
collect2: ld returned 1 exit status
make[4]: *** [perl.la] Error 1
make[4]: Leaving directory `/home/btdown/Desktop/xchat-2.6.0/plugins/perl'
make[3]: *** [all] Error 2
make[3]: Leaving directory `/home/btdown/Desktop/xchat-2.6.0/plugins/perl'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/btdown/Desktop/xchat-2.6.0/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/btdown/Desktop/xchat-2.6.0'
make: *** [all] Error 2

 
no clue where to go from here... ;(

---

### Post by niko_ on 2005-11-04
hi btdown, just type this:

> sudo apt-get install libperl-dev

and then your compilation will go flawless, 

cheers

---

### Post by Kyral on 2005-11-04
As for a backport, cool your jets. Its not even in Dapper yet :P

(Believe me I want this ;P)

---

### Post by Kyral on 2005-11-04
Wow, I just checked the package archives and it said that XChat is at 2.4.5

Did they just like jump a version number?

---

### Post by niko_ on 2005-11-04
I dont care about, even breezy didnt have all packages latest version when it got released. As long as you have some unix knowledge its no problem to download sources, configure & compile, install some devel packages if needed for compile and then you have the latest version of your program, which is cool ;)

---

### Post by btdown on 2005-11-04
Niko,
 
You were right--It works! Thanks for your help!
-BT
 
For those interested, I had to install the following packages in order for it to compile and install properly:
 
build-essential
libperl-dev
libgtk2.0-dev
python2.4-dev

---

### Post by akurashy on 2005-11-04
[quote=niko_]hi, thanks for letting me know its out :)
I downloaded, extracted the source, put the patch, configured, compiled
after that i removed the old xchat (*sudo apt-get remove xchat*) and then *sudo make install* and it works without problems. Maybe i will write a howto if this is so serious. If you got some compilation errors, let me know, maybe i can help.

anyways i attached the screenshot for 'proof':

[ATTACH]3360[/ATTACH][/quote] 
hey nicko, i got a annoying error with GLIB, how can i fix it, i really want 2.6.0 :)

Edit: opps nevermind didn't saw this, THANKS BTDOWN & nicko :)

---

### Post by akurashy on 2005-11-04
The compilation when smooth, very i say, i'm kinda troubled, i lost my xchat icon in the menus, how can i bring it back? =/

---

### Post by btdown on 2005-11-04
I rebooted and it the icon was back in the menu..perhaps you could just restart gnome, though.

---

### Post by akurashy on 2005-11-04
[quote=btdown]I rebooted and it the icon was back in the menu..perhaps you could just restart gnome, though.[/quote]

kk that worked :) thanks

---

### Post by jdong on 2005-11-11
Not in Dapper yet....

---

### Post by lisa-m on 2005-11-15
while trying to make xchat after i did configure i got the following error:
make  all-recursive
make[1]: Entering directory `/home/user/xchat-2.6.0'
Making all in po
make[2]: Entering directory `/home/user/xchat-2.6.0/po'
test ! -f ./xchat.pot || \
  test -z "nl.gmo zh_TW.gmo" || make nl.gmo zh_TW.gmo
make[3]: Entering directory `/home/user/xchat-2.6.0/po'
rm -f nl.gmo && : -c --statistics -o nl.gmo nl.po
mv: cannot stat `t-nl.gmo': No such file or directory
make[3]: *** [nl.gmo] Error 1
make[3]: Leaving directory `/home/user/xchat-2.6.0/po'
make[2]: *** [stamp-po] Error 2
make[2]: Leaving directory `/home/user/xchat-2.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/user/xchat-2.6.0'
make: *** [all] Error 2

at the end of configure i had no error and had the following output
xchat 2.6.0

Building GTK+ Interface .... : yes
Building TEXT Interface .... : no

PLUGINS: Perl: yes Python: yes TCL: no DBUS: yes

mmx tinting ......... : yes
XShm tinting ........ : no      plugin interface .... : yes
text backend ........ : pango   nls/gettext ......... : yes
openssl support ..... : no      ipv6 support ........ : no

The binary will be installed in /usr/local/bin

configure complete, now type 'make' and pray.

anyone can provide information regarding this please. I don't have xchat on my ubuntu since it's a server install. So I'm starting fresh. I taught i got all the neccesary libs and packages needs to build this. and configure gave me no errors about any packages or missing libs.

---

### Post by donar73 on 2005-11-15
It's in the Dapper-Repositories now! :)

---

### Post by Technoviking on 2005-11-15
Aprroved.

Mike

---

### Post by lisa-m on 2005-11-15
I'm on Breezy Badger 5.10, how can i get it?

---

### Post by ssam on 2005-11-15
have a read of this

[http://ubuntuforums.org/showthread.php?t=40291](http://ubuntuforums.org/showthread.php?t=40291)

---

### Post by Technoviking on 2005-11-15
[QUOTE=lisa-m]I'm on Breezy Badger 5.10, how can i get it?[/QUOTE]
It will show up in the backports soon, just make sure the backport lines in your /etc/apt/sources.list are uncommented.

Mike

---

### Post by lisa-m on 2005-11-15
ye i had  those two line enabled from a long time, since they were announced. Is there anything in the backports at the moment?

---

### Post by Technoviking on 2005-11-15
[QUOTE=lisa-m]ye i had  those two line enabled from a long time, since they were announced. Is there anything in the backports at the moment?[/QUOTE]
Not yet.

Mike

---

### Post by lisa-m on 2005-11-21
it's been more then a week now, when are the backports actually going to have content in them?

---

### Post by akurashy on 2005-11-21
I did this package, if you are still in the look for it

[http://davidgonz.com/xchat_2.6.0-1_i386.deb](http://davidgonz.com/xchat_2.6.0-1_i386.deb)

enjoy :)

---

### Post by Pablo_Escobar on 2005-11-21
Xchat 2.6.0 is very easy to compile by hand :) Try it :)

---

### Post by lisa-m on 2005-11-21
it's not just about xchat, i'm asking in general, when will the backports have something in them. cause so far i don't see anything that was accepted into backports. So that's all i wanted to know, if there' a problem with backports or it takes time to add new content..

---

### Post by veloct on 2005-11-21
I downloaded the .deb file but I'm going to compile it myself first.  It's been a while so I want to have some fun.  

./configure <file>
make
sudo make install (may just try checkinstall)

if I'm remembering right.  If i want to "make clean" afterwards, do I need to sudo that command?

---

### Post by jdong on 2005-11-21
[QUOTE=lisa-m]it's not just about xchat, i'm asking in general, when will the backports have something in them. cause so far i don't see anything that was accepted into backports. So that's all i wanted to know, if there' a problem with backports or it takes time to add new content..[/QUOTE]

I've already sent a good 30 backports off to James Troup, the Backports archive administrator. When he adds them in, it's really hard for me to tell...

On a sidenote, he did add the evms backport today to the build system, which is a good sign of things to come! :)

---

### Post by imagine on 2005-11-22
It's there, it's there \o/

---

### Post by btdown on 2005-11-23
Have a quick question: I was able to compile it myself and it works great. Now that its in the repository, should I install the repository version? if so, should I just install over top of the compiled version I made, or how would I uninstall the compiled version?

---

### Post by SInDrOoM on 2005-12-05
Hi everybody! I am new in ubuntu system! I have the same problem like lisa-m !

> pprimoz@ubuntu:~/xchat-2.6.0$ make
make  all-recursive
make[1]: Entering directory `/home/pprimoz/xchat-2.6.0'
Making all in po
make[2]: Entering directory `/home/pprimoz/xchat-2.6.0/po'
test ! -f ./xchat.pot || \
  test -z "nl.gmo zh_TW.gmo" || make nl.gmo zh_TW.gmo
make[3]: Entering directory `/home/pprimoz/xchat-2.6.0/po'
rm -f nl.gmo && : -c --statistics -o nl.gmo nl.po
mv: statusa ,t-nl.gmo` ni mo&#269; ugotoviti s stat: No such file or directory
make[3]: *** [nl.gmo] Error 1
make[3]: Leaving directory `/home/pprimoz/xchat-2.6.0/po'
make[2]: *** [stamp-po] Error 2
make[2]: Leaving directory `/home/pprimoz/xchat-2.6.0/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/pprimoz/xchat-2.6.0'
make: *** [all] Error 2

What should I do? Please help me! :D

---

### Post by vbmaster on 2006-01-12
Can somebody help me?

I'm tring to compiling it (xchat 2.6 of course) and i always get this error:

```

checking for GLIB - version >= 2.0.3...
*** 'pkg-config --modversion glib-2.0' returned 2.9.0, but GLIB (2.8.3)
*** was found! If pkg-config was correct, then it is best
*** to remove the old version of GLib. You may also be able to fix the error
*** by modifying your LD_LIBRARY_PATH enviroment variable, or by editing
*** /etc/ld.so.conf. Make sure you have run ldconfig if that is
*** required on your system.
*** If pkg-config was wrong, set the environment variable PKG_CONFIG_PATH
*** to point to the correct configuration files
no
configure: error: "Cannot find glib"

```

But I have glib 2.0 and glib 1.2 too!

What can I do to solve this?

---

### Post by arpunk on 2006-01-12
Do you have the glib development package installed?

---

### Post by vbmaster on 2006-01-12
Yep.

I have this ones installed:

```

libglib2.0-0 - The GLib library of C routines
libglib2.0-data - Common files for GLib library
libglib-perl
libglib1.2 - The GLib library of C routines
libglib1.2-dev - Development files for GLib library
libglib2.0-0-dbg - The GLib libraries and debugging symbols
libglib2.0-dev - Development files for the GLib library

```

---

