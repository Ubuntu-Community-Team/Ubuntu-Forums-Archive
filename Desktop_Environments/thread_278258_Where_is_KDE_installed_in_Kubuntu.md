---
title: "Where is KDE installed in Kubuntu?"
date: 2006-10-16
forum: Desktop Environments
---

### Post by kipe on 2006-10-16
Hello, i'm trying to compile desklist ([http://www.kde-apps.org/content/show.php?content=32089](http://www.kde-apps.org/content/show.php?content=32089)) from the source. Desklist is a plugin for kopete, and the ./configure script want to be specified the path to the KDE Headers (./configure --prefix=/path/to/KDE/3.5 ). Does anybody know where are the KDE Headers and KDE installation dir? It's not in the /opt folder for sure. Help!

---

### Post by kipe on 2006-10-16
Someone help ](*,)

---

### Post by kuja on 2006-10-16
KDE is installed under the prefix /usr. The headers are in the folder /usr/lib/kde3. You likely want to set the KDEDIR variable rather than prefix.

export KDEDIR=/usr/lib/kde3 && ./configure --prefix=/usr

---

### Post by BenoL on 2006-10-16
I searched for "kde" with the KDE Find files tool and got /usr/include and /usr/share/applications. I know, that kde libraries are stored in /usr/lib/kde3

---

### Post by kipe on 2006-10-17
Thank you for your answers! But unfortunatelly they didn't match the correct path to the KDE headers! The error is still the same:

"checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix! "

So, if someone know how to compile damn desklist plugin for kopete please write or there is no way to install it on Kubuntu !!!

---

### Post by kerry_s on 2006-10-17
Did you install them? (sudo apt-get install kde-devel)

But i don't think you need all that, does it say anything in the read me file as to what it depends on. I'm thinking that since it's for kopete, you might just need kopete-dev.

---

### Post by kipe on 2006-10-17
I didn't have kde-dev packages :mrgreen: . I'll download them and I will try again. Maybe that is the problem ... 
Anyway the README Says: 

Just do
        ./configure --prefix=/path/to/kde/3.5
        make
        make install (as super user)
in this directory.

That's it. I'll try after installation of kde-dev and I'll write back

---

### Post by kipe on 2006-10-17
OK, I have some advance, but it's very little! I've installed the kde-dev and the configure script now finish without errors :) BUT the make drop this: 

grep: /usr/lib/libfam.la: No such file or directory
/bin/sed: can't read /usr/lib/libfam.la: No such file or directory
libtool: link: `/usr/lib/libfam.la' is not a valid libtool archive
make[2]: *** [kopete_desklist.la] Error 1
make[2]: Leaving directory `/tmp/desklist/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tmp/desklist'
make: *** [all] Error 2

I have trying (apt-cache search libfam) and the result is:

libgamin-dev - Development files for the gamin client library
libgamin0 - Client library for the gamin file and directory monitoring system
libfam-dev - client library to control the FAM daemon - development files
libfam-ruby - Ruby Extension for the FAM C library
libfam0 - client library to control the FAM daemon
libfame-0.9 - A video encoding library - runtime files
libfame-dev - A video encoding library - devel files

I've trying to install libfam0 but the apt-get want's to remove about 180 pkgs (Whole KDE and others) to install this package. Tell me what to do! Or maybe the error is somewhere else. WIll someone who have some time try to install the damn plugin for his/hers Kopete. The plugin website is: [http://www.kde-apps.org/content/show.php?content=32089](http://www.kde-apps.org/content/show.php?content=32089)

---

### Post by kuja on 2006-10-17
Oh, I guess I should have mentioned that. I (wrongly) assumed you had the -dev packages you needed... 

It looks like the packages libfam0 and libgamin0 conflict. You can only have one of them installed. At any rate. You need the -dev package. You either need libfam-dev or libgamin-dev (I think either will do, but you can't have both because they conflict). I'm wondering where the conflict would be installing that package. Perhaps you could let it remove those packages. Copy down which ones it is doing, and reinstall them after libfam-dev is installed. I would compile it myself, but the results wouldn't be 100% the same, seeing as I have a massive amount of development packages installed already, and plus I'm running Kubuntu Edgy Eft (assuming you're not?)

---

### Post by kipe on 2006-10-18
> **kuja said:**
> Oh, I guess I should have mentioned that. I (wrongly) assumed you had the -dev packages you needed... 

It looks like the packages libfam0 and libgamin0 conflict. You can only have one of them installed. At any rate. You need the -dev package. You either need libfam-dev or libgamin-dev (I think either will do, but you can't have both because they conflict). I'm wondering where the conflict would be installing that package. Perhaps you could let it remove those packages. Copy down which ones it is doing, and reinstall them after libfam-dev is installed. I would compile it myself, but the results wouldn't be 100% the same, seeing as I have a massive amount of development packages installed already, and plus I'm running Kubuntu Edgy Eft (assuming you're not?)

Thank you!!! It work's finally! I've just installed libgamin-dev like you sad and everything passed smoothly. Make compiles without errors and everything works fine. Thank you again for your help. :mrgreen:

---

### Post by jpapciak on 2007-03-09
I guess since this is the same problem, maybe one of you could help me with this:

checking X11/extensions/scrnsaver.h usability... no
checking X11/extensions/scrnsaver.h presence... no
checking for X11/extensions/scrnsaver.h... no
configure: error: X Screensaver extension header files not found!

That's what I'm getting when I ./configure in Terminal.  Try to be easy on me, I'm very new to Linux, but any help would be greatly appreciated, thanks!

---

