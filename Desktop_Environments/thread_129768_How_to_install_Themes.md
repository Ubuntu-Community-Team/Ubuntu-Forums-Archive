---
title: "How to install Themes"
date: 2006-02-14
forum: Desktop Environments
---

### Post by tagg3rx on 2006-02-14
Hi all,
I have downloaded a few KDE themes from kde-look.org and extracted the tar.gz

When i go into settings - appearence and themes - theme manager 
And choose Install theme I browse to both the folder with the tar.gz and the extracted folders and neither show up as a theme file.

How do you install themes?

Thanks

---

### Post by Neo Ex on 2006-02-14
You have to compile it:
(from a terminal)
$ ./configure
$ make
# make install

or

$ sudo make install

If you receive some error, try installing these packages: build-essential, automake1.x, autoconf, cpp-x.x, gcc-x.x, g++-x.x, xlibs-dev, libx11-dev, kdelibs4-dev, kdebase-dev, libqt3-mt-dev, linux-kernel-headers (maybe some of these packages isn't required).

---

### Post by tagg3rx on 2006-02-14
I tried and got the following:

penguin@95-ubuntu:~/Themes/snowballkdetheme$ ls
konqueror  ksplash  kthememgr
penguin@95-ubuntu:~/Themes/snowballkdetheme$ ./configure
bash: ./configure: No such file or directory
penguin@95-ubuntu:~/Themes/snowballkdetheme$ sudo make install
make: *** No rule to make target `install'.  Stop.
penguin@95-ubuntu:~/Themes/snowballkdetheme$        

I think those steps are for when you want to make an installer I dont believe you need to create and installer to add a theme.
But i may be mistaken.

As you can see there are no files to build in the root dir of the theme
Here is the tree
3 main dirs
[COLOR="Magenta"]konqueror/    ksplash/   kthememgr/[/COLOR]
~/Themes/snowballkdetheme/konqueror/tiles$ ls
[COLOR="Magenta"]bg_snowball.png[/COLOR]

penguin@95-ubuntu:~/Themes/snowballkdetheme/ksplash/pics$ ls
[COLOR="Magenta"]splash_active_bar.png  splash_inactive_bar.png
splash_bottom.png      splash_top.png[/COLOR]

penguin@95-ubuntu:~/Themes/snowballkdetheme/kthememgr/Themes$ ls
[COLOR="Magenta"]Snowball.ktheme[/COLOR]

---

### Post by Neo Ex on 2006-02-14
Ops, I've thought you mean the styles... sorry, I can't help you: I've never downloaded a theme, and now KDE Look is down...

---

### Post by analyticalman on 2006-02-14
I can't check because kde-look won't load at the moment but I didn't think that you had to extract the theme.  just put it where you want and go to the theme manager.  Anyway, KDE-Look always has "how to install" instructions next to the download icon.  Sorry if my memory is faulty

---

### Post by FlakJacket on 2006-02-14
What does the theme change exactly?  I have installed all types recently (I like me eye candy)  but what type of theme?

Flak

---

### Post by tagg3rx on 2006-02-15
Ok KDE-look.org is back up - i have looked there site over and cant find a how to install section so I'll run the steps by you guys.

So I download the blue ice theme from:
[http://www.kde-look.org/content/show.php?content=13074](http://www.kde-look.org/content/show.php?content=13074)
I'll download the source as .deb never work for me

Then I extract the tar.gz into my ~/Themes folder
in a shell I go to the extracted folder and type

./configure
and a bunch of stuff happens... this is looking promising

The last couple of lines concern me
> configure: WARNING: libjpeg not found. disable JPEG support.
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.2) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.


but i'll continue by typing make

and i get
> penguin@95-ubuntu:~/Themes/kwin-dark-blueice-4$ make
make: *** No targets specified and no makefile found.  Stop.



And I try make install
> penguin@95-ubuntu:~/Themes/kwin-dark-blueice-4$ make install
make: *** No rule to make target `install'.  Stop.


So there you have it 
Building and making are still way fuzzy to me (ie i have never made it work) so any help would be appriciated.

So I download and extract the deb package and i find a file named debian-binary - i click on it - it opens up in kate and all it reads is:
2.0

Help plz
Thanks

---

### Post by FlakJacket on 2006-02-15
in apt you need kdebase-dev and libqt3-headers.  I think you might need to install a different package before it will let you install kdebase-dev post the dependency error if you get it.

Hope that helps,
Flak

---

### Post by tagg3rx on 2006-02-15
Linux is simple.....  Ai Vai!

Ok installing everything mentoned here
build-essential, 
automake1.x, 
autoconf, 
cpp-x.x, 
gcc-x.x, 
g++-x.x, 
xlibs-dev, 
libx11-dev, 
kdelibs4-dev, 
kdebase-dev, 
libqt3-mt-dev, 
linux-kernel-headers

kdebase-dev and anything that says libqt3

I feel like a sheep - i'd like to understand what all this rigamaroo is i just installed but i'm afraid of the answers :D 

I'll try and recompile once i finish installing these 72 packages and post the results.

Cheers

---

### Post by tagg3rx on 2006-02-15
Ok I think I'm close the make install is complete - my question is 

now what do i do next

> penguin@95-ubuntu:~/Themes/kwin-dark-blueice-4$ sudo make install
Making install in kwin
make[1]: Entering directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin'
Making install in .
make[2]: Entering directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin'
make[3]: Entering directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin'
test -z "/usr/local/kde/lib/kde3" || mkdir -p -- . "/usr/local/kde/lib/kde3"
 /bin/sh ../libtool --silent --mode=install /usr/bin/install -c -p  'kwin3_dark-blueice.la' '/usr/local/kde/lib/kde3/kwin3_dark-blueice.la'
PATH="$PATH:/sbin" ldconfig -n /usr/local/kde/lib/kde3
test -z "/usr/local/kde/share/apps/kwin" || mkdir -p -- . "/usr/local/kde/share/apps/kwin"
 /usr/bin/install -c -p -m 644 'dark-blueice.desktop' '/usr/local/kde/share/apps/kwin/dark-blueice.desktop'
make[3]: Leaving directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin'
make[2]: Leaving directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin'
Making install in config
make[2]: Entering directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin/config'
make[3]: Entering directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin/config'
test -z "/usr/local/kde/lib/kde3" || mkdir -p -- . "/usr/local/kde/lib/kde3"
 /bin/sh ../../libtool --silent --mode=install /usr/bin/install -c -p  'kwin_dark-blueice_config.la' '/usr/local/kde/lib/kde3/kwin_dark-blueice_config.la'
PATH="$PATH:/sbin" ldconfig -n /usr/local/kde/lib/kde3
make[3]: Nothing to be done for `install-data-am'.
make[3]: Leaving directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin/config'
make[2]: Leaving directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin/config'
make[1]: Leaving directory `/home/penguin/Themes/kwin-dark-blueice-4/kwin'
make[1]: Entering directory `/home/penguin/Themes/kwin-dark-blueice-4'
make[2]: Entering directory `/home/penguin/Themes/kwin-dark-blueice-4'
make[2]: Nothing to be done for `install-exec-am'.
make[2]: Nothing to be done for `install-data-am'.
make[2]: Leaving directory `/home/penguin/Themes/kwin-dark-blueice-4'
make[1]: Leaving directory `/home/penguin/Themes/kwin-dark-blueice-4'
penguin@95-ubuntu:~/Themes/kwin-dark-blueice-4$                                                                    

---

### Post by FlakJacket on 2006-02-15
now you should be able to select it from the menu that allows you to select theme.

Flak

EDIT: That's a window decoration so go to system settings > Appearance > Window Decorations > and it should be in the dropdown menu.

---

