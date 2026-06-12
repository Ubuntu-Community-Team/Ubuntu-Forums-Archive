---
title: "I'm an idiot... I can't install a theme..."
date: 2005-09-19
forum: Desktop Environments
---

### Post by mulletman13 on 2005-09-19
Hey all, trying to install baghira, and various other themes from KDE-look, and I really can't figure out how to do it.  I untar'ed the baghira source file, and typed in what they said to on the website only to get the following :

```
root@cookiesh:/home/mm13/Desktop/baghira-0.6e # ./configure --prefix='kde-config --prefix' --disable-debug --enable-final
configure: error: expected an absolute directory name for --prefix: kde-config --prefix
root@cookiesh:/home/mm13/Desktop/baghira-0.6e # ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
``` 

I've tried to just install the .deb file for debian -- but that's not working for the life of me.  

*sigh*

I'm stupid... please help.

---

### Post by aysiu on 2005-09-19
Follow these instructions:

[http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories](http://www.frankandjacq.com/ubuntuguide/5.04/#extrarepositories)

Then you can ```
sudo apt-get update
sudo apt-get install kwin-baghira
```

---

### Post by bsussman on 2005-09-19
I'm no expert but I bet that

....'kde-config --prefix'.....

should prolly be 

.....'kde-config'......

---

### Post by Xian on 2005-09-19
Since not every theme will have an applicable .deb file you should at some point consider installing the 'build-essential' package in apt. This will allow you to install the source files of other themes.

```
$ sudo apt-get install build-essential
```

---

### Post by Freddy on 2005-09-19
Don't do as in previous posts, the Baghira in the repos i quite old and the new one is much better.

What you are missing is the compiler and other build-essentials (such as make), just type "sudo apt-get install build-essential" (hope I spelled it right, if I didn't "sudo apt-get install build-essen*" should do the trick) in your console and you should be able to start the compile of the Baghira source. Maybe you need other stuff to like kde-devels and such from your repos but everything you need for a succeful compile should be there.  /// Freddan

Edit: I can't win with this guy hes always posting while I'm writing, maybe I should use more then one finger on each hand ;)

---

### Post by mulletman13 on 2005-09-19
[QUOTE=Freddy]Don't do as in previous posts, the Baghira in the repos i quite old and the new one is much better.

What you are missing is the compiler and other build-essentials (such as make), just type "sudo apt-get install build-essential" (hope I spelled it right, if I didn't "sudo apt-get install build-essen*" should do the trick) in your console and you should be able to start the compile of the Baghira source. Maybe you need other stuff to like kde-devels and such from your repos but everything you need for a succeful compile should be there.  /// Freddan

Edit: I can't win with this guy hes always posting while I'm writing, maybe I should use more then one finger on each hand ;)

Edit2: No need for any prefix on you first config, just ./configure no more.[/QUOTE]
 Thanks a ton guys... I wonder why that stuff wasnt installed initially.... anyways now it gets farther, but I get this problem:

checking for crt_externs.h... no
checking for _NSGetEnviron... no
checking for vsnprintf... yes
checking for snprintf... yes
checking for X... configure: error: Can't find X includes. Please check your installation and add the correct paths!

Damn... I don'thave whatever this 'x' is.... *sigh

---

### Post by Xian on 2005-09-19
Install one or all of these packages:

x-dev
libx11-dev
xlibs-dev

---

### Post by mulletman13 on 2005-09-19
[QUOTE=Xian]Install one or all of these packages:

x-dev
libx11-dev
xlibs-dev[/QUOTE]
 Thanks everybody for the replies.... but a new problem has come up:

checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!

***sigh***  Is everything this difficult?

---

### Post by GoldBuggie on 2005-09-19
install libqt3-headers

and about everything beeing this difficult...well when you got most things installed you don
t need to install them again. And when you start to compile things there are some things that are often needed like the qt3 header files. It will get easier with time i'm sure

---

### Post by Ptero-4 on 2005-09-19
[QUOTE=GoldBuggie]install libqt3-headers

and about everything beeing this difficult...well when you got most things installed you don
t need to install them again. And when you start to compile things there are some things that are often needed like the qt3 header files. It will get easier with time i'm sure[/QUOTE]
 To install ANY kde themes you'll need the build-essential package, then the X dev stuff, then the qt dev stuff and finally the kdebase dev package. Also don't install the baghira theme from the repos, that version (and anything older than 0.6a) have a nasty bug that under bigendian boxes (a.k.a: Macs) renders custom widget coloring useless. The version at baghira.sf.net is fixed already.

And when compiling software for kde you have to put ./configure --prefix=`kde-config --prefix` , this instructs the ./configure script to install the binaries and libraries in the directory indicated by the kde-config script. The kde-config script is a script created by KDE to tell it's apps where the kde libs are.

---

### Post by mulletman13 on 2005-09-19
[QUOTE=GoldBuggie]install libqt3-headers

and about everything beeing this difficult...well when you got most things installed you don
t need to install them again. And when you start to compile things there are some things that are often needed like the qt3 header files. It will get easier with time i'm sure[/QUOTE]
 Grrrr.... this is so ridiculously frustrating.

I put the debian servers in my sources.list file, and ran apt-get install kwin-baghira............. this installed a ton of different things and finally got to "setting up baghira"... then back to the control prompt.

Anyways, now I have no idea if it's set up or anything, I go to change my theme/search my system for 'baghira' and can't find *anything* having to do with this.

... *sigh

---

### Post by mulletman13 on 2005-09-19
...........  all righty, I installed all of those things that I've been told to, ran everything....... is it normal to take a real long time to 'make' the file?  

Making install in kickermenu
make[1]: Entering directory `/home/mm13/Desktop/baghira-0.6e/kickermenu'
make[2]: Entering directory `/home/mm13/Desktop/baghira-0.6e/kickermenu'
/bin/sh ../admin/mkinstalldirs /usr/lib/kde3
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  b_menu_panelapplet.la /usr/lib/kde3/b_menu_panelapplet.la
PATH="$PATH:/sbin" ldconfig -n /usr/lib/kde3
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/mm13/Desktop/baghira-0.6e/kickermenu'
make[1]: Leaving directory `/home/mm13/Desktop/baghira-0.6e/kickermenu'
make[1]: Entering directory `/home/mm13/Desktop/baghira-0.6e'
make[2]: Entering directory `/home/mm13/Desktop/baghira-0.6e'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/mm13/Desktop/baghira-0.6e'
make[1]: Leaving directory `/home/mm13/Desktop/baghira-0.6e'


...........  that is what the 'make install' gets to... then back to command prompt.  Where... in god's name does this 'install' to.... I go to try to apply another theme, and it's NOWHERE to be seen.

I can't believe something so trivial as installing a theme is made with so many steps.  :-\

Any help would be needed.  And why can't precompiled themes be sent out.... it doesnt seem like it depends on computer hardware... blah

---

### Post by mulletman13 on 2005-09-21
*bump*

Hrmm... I don't know the extension for a theme file, nor do I know where this may install the theme at... can somebody please help with this?  This is making me feel ridiculously stupid :(

---

### Post by Freddy on 2005-09-21
Baghira isn't really a theme, a theme is a wallpaper, some icons, style, windec and color maybe all or just some of those things. Baghira is a style and a windec and you find it under those 2 tabs in kcontrol.  /// Freddan

---

### Post by TuxRace on 2005-10-06
[QUOTE=mulletman13]Thanks everybody for the replies.... but a new problem has come up:
checking whether uic supports -L ... yes
checking whether uic supports -nounload ... yes
checking if Qt needs -ljpeg... no
checking for rpath... yes
checking for KDE... configure: error:
in the prefix, you've chosen, are no KDE headers installed. This will fail.
So, check this please and use another prefix!
***sigh***  Is everything this difficult?[/QUOTE]
bump!

Can anyone please help me and him? I have had the same problems as him and it would be very nice if i could get baghira to work

---

### Post by f1dave on 2005-10-06
When I installed baghira some time ago, it showed up in the style and window decoration sections of kcontrol no problem.

There's also a (somewhat older i believe) version of baghira in the backports.

---

### Post by mulletman13 on 2005-10-06
Heh I never posted a follow up...

Yea it turns out after I installed it, I was looking in the 'Theme' section.... apparently Baghira is a Windows Decoration, and a Style.... whoops :???: 

Thanks for the help and I hope it helps you :)

---

