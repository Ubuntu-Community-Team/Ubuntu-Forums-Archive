---
title: "Installing compiz fusion 0.7.2 - is there a simple way"
date: 2008-03-09
forum: Desktop Effects &amp; Customization
---

### Post by aashay on 2008-03-09
I'm currently trying to install compiz fusion 0.7.2 from source. 
The first snag was the absence of x11-xcb, which I *think* I have corrected. (Not sure how to check)
Now atleast ./configure finishes to completion without any errors.
However, I get multiple errors while 'make'ing it.
Is there a simpler way to install it? When can we expect it to hit the repos?

```

make  all-recursive
make[1]: Entering directory `/home/aashay/temp/compiz-0.7.2'
Making all in include
make[2]: Entering directory `/home/aashay/temp/compiz-0.7.2/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/aashay/temp/compiz-0.7.2/include'
Making all in src
make[2]: Entering directory `/home/aashay/temp/compiz-0.7.2/src'
gcc -DHAVE_CONFIG_H -I. -I.. -I/usr/local/include -I/usr/include/libxml2 -I/usr/include/startup-notification-1.0 -I../include -I../include -DPLUGINDIR=\"/usr/local/lib/compiz\" -DIMAGEDIR=\"/usr/local/share/compiz\" -DMETADATADIR=\"/usr/local/share/compiz\"    -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -MT main.o -MD -MP -MF .deps/main.Tpo -c -o main.o main.c
In file included from main.c:37:
../include/compiz-core.h:48:19: error: GL/gl.h: No such file or directory
../include/compiz-core.h:49:20: error: GL/glx.h: No such file or directory
In file included from main.c:37:
../include/compiz-core.h:209: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;defaultColor&#8217;
../include/compiz-core.h:1063: error: expected specifier-qualifier-list before &#8216;GLenum&#8217;
../include/compiz-core.h:1317: error: expected specifier-qualifier-list before &#8216;GLfloat&#8217;
../include/compiz-core.h:1328: error: expected specifier-qualifier-list before &#8216;GLushort&#8217;
../include/compiz-core.h:1615: error: expected specifier-qualifier-list before &#8216;GLuint&#8217;
../include/compiz-core.h:1655: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GLenum&#8217;
../include/compiz-core.h:1656: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GLenum&#8217;
../include/compiz-core.h:1743: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;GLubyte&#8217;
../include/compiz-core.h:1743: error: expected &#8216;;&#8217;, &#8216;,&#8217; or &#8216;)&#8217; before &#8216;*&#8217; token
../include/compiz-core.h:1746: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GLXDrawable&#8217;
../include/compiz-core.h:1750: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GLXDrawable&#8217;
../include/compiz-core.h:1753: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GLXDrawable&#8217;
../include/compiz-core.h:1758: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GLXDrawable&#8217;
../include/compiz-core.h:1780: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;*&#8217; token
../include/compiz-core.h:1783: warning: type defaults to &#8216;int&#8217; in declaration of &#8216;GLXPixmap&#8217;
../include/compiz-core.h:1783: error: &#8216;GLXPixmap&#8217; declared as function returning a function
../include/compiz-core.h:1783: warning: function declaration isn&#8217;t a prototype
../include/compiz-core.h:1785: error: expected &#8216;)&#8217; before &#8216;texture&#8217;
../include/compiz-core.h:1786: error: expected &#8216;)&#8217; before &#8216;texture&#8217;
../include/compiz-core.h:1788: error: expected &#8216;)&#8217; before &#8216;n&#8217;
../include/compiz-core.h:1790: error: expected &#8216;)&#8217; before &#8216;n&#8217;
../include/compiz-core.h:1792: error: expected &#8216;)&#8217; before &#8216;target&#8217;
../include/compiz-core.h:1794: error: expected &#8216;)&#8217; before &#8216;target&#8217;
../include/compiz-core.h:1798: error: expected &#8216;)&#8217; before &#8216;target&#8217;
../include/compiz-core.h:1805: error: expected &#8216;)&#8217; before &#8216;n&#8217;
../include/compiz-core.h:1807: error: expected &#8216;)&#8217; before &#8216;n&#8217;
../include/compiz-core.h:1809: error: expected &#8216;)&#8217; before &#8216;target&#8217;
../include/compiz-core.h:1811: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;*&#8217; token
../include/compiz-core.h:1811: error: expected &#8216;)&#8217; before &#8216;target&#8217;
../include/compiz-core.h:1812: error: expected &#8216;)&#8217; before &#8216;target&#8217;
../include/compiz-core.h:1817: error: expected &#8216;)&#8217; before &#8216;target&#8217;
../include/compiz-core.h:2035: error: expected specifier-qualifier-list before &#8216;GLint&#8217;
../include/compiz-core.h:2400: error: expected declaration specifiers or &#8216;...&#8217; before &#8216;GLenum&#8217;
../include/compiz-core.h:2561: error: expected specifier-qualifier-list before &#8216;GLint&#8217;
../include/compiz-core.h:3138: error: expected specifier-qualifier-list before &#8216;GLushort&#8217;
main.c:47: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;defaultColor&#8217;
main.c: In function &#8216;compLogMessage&#8217;:
main.c:116: error: &#8216;CompDisplay&#8217; has no member named &#8216;logMessage&#8217;
make[2]: *** [main.o] Error 1
make[2]: Leaving directory `/home/aashay/temp/compiz-0.7.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aashay/temp/compiz-0.7.2'
make: *** [all] Error 2

```

---

### Post by aashay on 2008-03-09
Okay, looks like its installing fine now
This is what I had to do:
```

git-clone git://anongit.freedesktop.org/git/xorg/lib/libX11
cd libX11{version}
./autogen.sh --with-xcb
make
sudo make install

```
After this install the following with aptitude:
libgl1-mesa-dev
libglu-dev
python-pyrex

Also be sure to install compiz-bcop(from source)  before installing the plugins

I am still installing the plugins as I write this, hope it works
EDIT:```

aashay@kriz-jr:~/temp/libX11$ ccsm
Traceback (most recent call last):
  File "/usr/local/bin/ccsm", line 38, in <module>
    import compizconfig
ImportError: libX11-xcb.so.1: cannot open shared object file: No such file or directory
```
Didn't work... any ideas?

---

### Post by aashay on 2008-03-10
bump!

---

### Post by mrmiserable on 2008-03-10
here is link to someone with same problem as you on compiz and the guy says he thinks hardy will have 0.7 

also maybe something in the thread that can help 

[http://forum.compiz-fusion.org/showthread.php?t=7275](http://forum.compiz-fusion.org/showthread.php?t=7275)

---

### Post by FuturePilot on 2008-03-10
Yes, Compiz 0.7.2 is in Hardy which will be released in a little over a month. If you're up to waiting a bit it will be as simple as upgrading :)

---

### Post by Eclipse. on 2008-03-10
Theres a guide in this forum somewhere that allows you to install compiz from git bypassing x11-xcb problem that works.Im using it right now.

Do a search for it.;)

---

### Post by elyase on 2008-03-11
I got the same error message than you. After several tries I could, bypass the xcb problem (installed libX11-1.1.4) and all compiled and installed very well. I had to make some additional simbolic links to libX11 libraries and finally got to run ccsm and fusion-icon. But when i run compiz i got a sementation fault error. I asked Amaranth(one of CF packagers for Ubuntu(main one i think)) and he told me, that CF 0.7.2 **can not be installed** in Gutsy, he was even surprised it could compile well. The reason is that this version of CF needs a new version of X server that will be available in Hardy. So  waiting is the only solution i guess. :(

---

### Post by aashay on 2008-03-11
Seems I had x11-xcb installed correctly
pkg-config --modversion x11-xcb returned 1.1.3 (not anymore, cause I removed it)
Seems all I had to do is symlink some libraries.
Anyway, I have given up. Hope hardy make it all better :p
EDIT: 
> **Eclipse. said:**
> Theres a guide in this forum somewhere that allows you to install compiz from git bypassing x11-xcb problem that works.Im using it right now.

Do a search for it.;)
-Could not find it.
> here is link to someone with same problem as you on compiz and the guy says he thinks hardy will have 0.7

also maybe something in the thread that can help

[http://forum.compiz-fusion.org/showthread.php?t=7275](http://forum.compiz-fusion.org/showthread.php?t=7275)
-Looked promising, but didn't work (ccsm still gave the same error

---

