---
title: "Please help me in compiling window decoration"
date: 2005-11-10
forum: Desktop Environments
---

### Post by Navyblue on 2005-11-10
Hi huys,

I am running Kubuntu Breezy for AMD64. I am trying to compile some windows decoration from source. However, I have never been able to make it past the "make" command. I have installed the "build-essential" package."

Here is the installation intruction

> 
Basic Installation (from the console):
  - Step 1
      $ ./configure --prefix=`kde-config --prefix`
  - Step 2
      $ make
  - Step 3 (as root)
      # make install

If configure fails, check that you have both
the Qt and KDE development headers installed.

You need at least KDE 3.2 and QT 3.3.

Debian note: You may need to append
--with-qt-includes=/usr/include/qt3
to the configure line.


My question is:

Should I type  "./configure --prefix=`kde-config --prefix` --with-qt-includes=/usr/include/qt3"?

Or should I replace `kde-config --prefix' with something else?

If yes what should I replace them with?

---

### Post by asimon on 2005-11-10
[QUOTE=Navyblue]
My question is:

Should I type  "./configure --prefix=`kde-config --prefix` --with-qt-includes=/usr/include/qt3"?

Or should I replace `kde-config --prefix' with something else?
[/QUOTE]
--prefix=`kde-config --prefix` is fine and should do the right thing on any distro, no need to replace it with something else. (On Ubuntu the KDE prefix is by the way /usr)

--with-qt-includes should not be needed, qt should be found automatically.

Thus "./configure --prefix=`kde-config --prefix`" should be enough. But your version with --with-qt-includes=... should work too, the path is right for Kubuntu.

If you want a quick and dirty debian package for easier deinstallation later you can try checkinstall. Just install the "checkinstall" package (it's part of universe) and instead of calling 'make install' later just call 'checkinstall', it will ask some questions and builds a nice deb package for your program. I think there are some threads in this forum about checkinstall.
But 'make install' should of course work too. If you don't delete the source tree after installation a 'make uninstall' should work if you want someday to remove it again.

---

### Post by asimon on 2005-11-10
I forget something. The "build-essential" package will not be enough to be able to compile KDE window decorations. You should be able to install all needed packages with 
```
# apt-get build-dep kdeartwork-theme-window
```

kdeartwork-theme-window contains some standard KDE window decoration. The command above downloads and installs all packages which are needed to build those decorations from source (but will not install kdeartwork-theme-window itself). This should be enough for your window decoration too.

---

### Post by Navyblue on 2005-11-10
Hi,

Thanks a lot for your explaination. It now works. :)

---

### Post by Navyblue on 2005-11-10
A repeat post. :)

---

### Post by Navyblue on 2005-11-10
After a couple of try, I find ti didn't work too smoothly, although I can get the package installed, but I can't uninstall them, apparently there are some problem on whether to call my architecture AMD64 or x86_64.

```

dpkg: error processing /home/navyblue/Desktop/kwin-blueice-4/kwin-blueice-4_4-1_
x86_64.deb (--install):
 package architecture (x86_64) does not match system (amd64)
Errors were encountered while processing:
 /home/navyblue/Desktop/kwin-blueice-4/kwin-blueice-4_4-1_x86_64.deb

```

What can I do about this?

---

### Post by asimon on 2005-11-10
Did you made this packge with checkinstall? If yes, I think, when you call 'checkinstall' to build the package, checkinstall gives you an overview of the values it'll use for the package and the opportunity to change these.

Because checkinstall evidently picks up the wrong architecture you have to change it from x86_64 to amd64.

EDIT:
You could also try to force the installation of the package even if it has the wrong architecture with 'dpkg --force-architecture --install ...' but this is very dirty. Better build a new package with the right architecture.

---

### Post by Navyblue on 2005-11-10
It only manages to complete the "make install" step, it does get installed but I did not get the .deb file. It says something like the creation failed and give me the log file above. And thus I do not have a chance to do a for achitecture installation.

Now the theme get installed and I guess the only way to uninstall it is to "make unistall".

---

### Post by sutech on 2005-11-22
Hi, I have a problem to compile a window decoration.
I have a Breezy for AMD64 and I can't get past "make". Very similar problem.
It just stops during "make" and gives me these errors:
```
cc1plus: warning: command line option "-Wmissing-prototypes" is valid for Ada/C/ObjC but not for C++
/usr/include/qt3/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/include/qt3/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
make[3]: *** No rule to make target `/usr/lib64/kwin.la', needed by `libkwinaqua_config.la'.  Stop.
make[3]: Leaving directory `/home/sutech/kde-look/win_decorations/aquaosk-2.0/acqua/config'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/sutech/kde-look/win_decorations/aquaosk-2.0/acqua'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/sutech/kde-look/win_decorations/aquaosk-2.0'
make: *** [all] Error 2

```

Can someone help me, please?

---

### Post by robinharvey on 2006-07-25
OK, I came across the same error message as above:
```
package architecture (x86_64) does not match system (amd64)
```
.. and solved it by changing the architecture from the menu in the last step of the checkinstall process.  At first, I saw this:
```

0 -  Maintainer: [ root@localhost.localdomain ]
1 -  Summary: [ This package created by checkinstall, rch 25/7/06 ]
2 -  Name:    [ php52cvs2 ]
3 -  Version: [ 200607241830 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ x86_64 ]
8 -  Source location: [ php5.2-200607241830 ]
9 -  Alternate source location: [  ]

```
..and by changing value 8 to "amd64" (by typing "8" then "amd64") it then looked like this:
```

0 -  Maintainer: [ root@localhost.localdomain ]
1 -  Summary: [ This package created by checkinstall, rch 25/7/06 ]
2 -  Name:    [ php52cvs2 ]
3 -  Version: [ 200607241830 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ amd64 ]
8 -  Source location: [ php5.2-200607241830 ]
9 -  Alternate source location: [  ]

```
and it all worked just fine.  Right under my nose, really :)

--Robin

---

