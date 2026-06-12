---
title: "Compiz Fusion 0.6.0. stable is out (how-to included)! should we wait for repo update?"
date: 2007-10-22
forum: Desktop Effects &amp; Customization
---

### Post by likeatim on 2007-10-22
a how-to for a MANUAL update is here: [http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html](http://phorolinux.com/how-to-install-compiz-fusion-060-from-sources-on-ubuntu-710-gutsy-gibbon.html)
or should we wait for the repos?

cheers,


likeatim

---

### Post by ThrobbingBrain66 on 2007-10-22
After release, Ubuntu only provides bug and security fixes.  There's a chance it could get backported, but don't count on it.

You can always wait for Trevino to add a Gutsy Eye Candy repo as well.

---

### Post by likeatim on 2007-10-22
half a year and compiz is stable now? 
I guess I'll go fo manual....

---

### Post by hopelessone on 2007-10-22
hi,

one step 3 i get errors: when **make**

shane@lotus:~/compiz-0.6.2$ make
make  all-recursive
make[1]: Entering directory `/home/shane/compiz-0.6.2'
Making all in include
make[2]: Entering directory `/home/shane/compiz-0.6.2/include'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/shane/compiz-0.6.2/include'
Making all in src
make[2]: Entering directory `/home/shane/compiz-0.6.2/src'
/bin/bash ../libtool --tag=CC   --mode=link gcc  -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -export-dynamic  -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE -lxslt -lxml2 -lstartup-notification-1   -lGL -lm 
gcc -g -O2 -Wall -Wpointer-arith -Wstrict-prototypes -Wmissing-prototypes -Wmissing-declarations -Wnested-externs -D_FORTIFY_SOURCE=2 -o compiz main.o privates.o texture.o display.o screen.o window.o event.o paint.o option.o plugin.o session.o fragment.o matrix.o cursor.o match.o metadata.o -Wl,--export-dynamic  -lXcomposite -lXdamage -lXfixes -lXrandr -lXinerama -lSM -lICE /usr/lib/libxslt.so -L/usr/lib /usr/lib/libxml2.so -lstartup-notification-1 -lGL -lm  

/usr/bin/ld: cannot find -lGL
collect2: ld returned 1 exit status
make[2]: *** [compiz] Error 1
make[2]: Leaving directory `/home/shane/compiz-0.6.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/shane/compiz-0.6.2'
make: *** [all] Error 2
shane@lotus:~/compiz-0.6.2$ 

what can i do?

thanks..

---

### Post by Sslaxx on 2007-10-22
Looks like you're missing the OpenGL development libraries. libgl1-mesa-dev might be what you need.

---

### Post by hopelessone on 2007-10-22
hi thanks for the reply...

synaptic says its there:
libgl1-mesa-dev 7.0.1 version 

any ideas?

---

### Post by jonray74 on 2007-10-22
The guidelines seems to be good though I haven't tried it yet, but how do you activate it using Kubuntu? The last part of it only shows how to activate it in GNOME, not KDE.

Thanks,
John

---

### Post by sdowney717 on 2007-10-22
some people are having trouble with the compile.
So, why not just wait for trevino to get his stuff going.
I expect it is going to happen sooner than later.

---

### Post by screaminj3sus on 2007-10-22
People were complaing about gaim for months and they never updated it in fiesty, I doubt they'll update compiz.

---

### Post by Hobo2021 on 2007-10-22
If you're having trouble getting it to compile you might not have all the dependencies - the article doesn't (apparently) list all that you need. I found a post that helped me get up at running though:

[http://forum.compiz-fusion.org/archive/index.php/t-1986.html](http://forum.compiz-fusion.org/archive/index.php/t-1986.html)

Specifically this chunk of stuff:
sudo apt-get install fakeroot automake1.9 x11proto-gl-dev subversion libtool librsvg2-dev libglitz-glx1-dev libglitz1-dev libneon25-dev intltool libxdamage-dev libglu1-mesa libglu1-mesa-dev libglu1-xorg-dev libxfixes-dev xlibs-dev icecc iceconf libxcomposite1 libxcomposite-dev libstartup-notification0-dev libwnck-dev fort77 gawk g77 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev libmetacity-dev libgnome-window-settings-dev python-pyrex python-gnome2 python-gnome2-dev python-dev libgnome-desktop-dev python-gtk2 python-gtk2 python-gtk2-dev libqt3-mt-dev libdbus-glib-1-dev libxslt1-dev

yay

You probably don't need all of those, but the ones around python, gnome and metacity are needed.

---

### Post by panurge77 on 2007-10-22
Isnt compiz 0.6 in the repos?  I guess not. The package name is misleading... it says 1:0.60 but it's a git from 20071008, so I guess it's not.

---

### Post by fart_flower on 2007-10-22
Compiz 6.0 is in the repositories, but Compiz Fusion is 5.2.  Recently Compiz 6.2 and Compiz Fusion 6.0 have been released.

It's the newer Compiz Fusion that people in this thread are referring to when they say "6.0".  (Basically the Compiz desktop is comprised of two major pieces.  Comp-fuzing?)

---

### Post by Xbehave on 2007-10-23
> **Hobo2021 said:**
> [http://forum.compiz-fusion.org/archive/index.php/t-1986.html](http://forum.compiz-fusion.org/archive/index.php/t-1986.html)

Specifically this chunk of stuff:
sudo apt-get install fakeroot automake1.9 x11proto-gl-dev subversion libtool librsvg2-dev libglitz-glx1-dev libglitz1-dev libneon25-dev intltool libxdamage-dev libglu1-mesa libglu1-mesa-dev libglu1-xorg-dev libxfixes-dev xlibs-dev icecc iceconf libxcomposite1 libxcomposite-dev libstartup-notification0-dev libwnck-dev fort77 gawk g77 build-essential cvs libpango1.0-dev libgtk2.0-dev libgconf2-dev libglitz-glx-dev librsvg2-dev checkinstall libglade2-dev libmetacity-dev libgnome-window-settings-dev python-pyrex python-gnome2 python-gnome2-dev python-dev libgnome-desktop-dev python-gtk2 python-gtk2 python-gtk2-dev libqt3-mt-dev libdbus-glib-1-dev libxslt1-dev

You probably don't need all of those, but the ones around python, gnome and metacity are needed.
what about kde users? any help, im going to try upgrading when i get home as CF is being a pain atm
o and to get it running in KDE which somebody asked about, i currently start all composting using a copy of beryl-manager from a fiesty repository

i dont suppose it would be possible to install multiple versions of CF? that way if the unsupported 1 doesnt work i can always use the official 1:S long shot i know

---

### Post by KhaaL on 2007-10-25
> **Xbehave said:**
> what about kde users? any help, im going to try upgrading when i get home as CF is being a pain atm
o and to get it running in KDE which somebody asked about, i currently start all composting using a copy of beryl-manager from a fiesty repository

i dont suppose it would be possible to install multiple versions of CF? that way if the unsupported 1 doesnt work i can always use the official 1:S long shot i know

I have some serious problems with CF running under KDE (plugins randomly unloading at startup) which I haven't managed to cure yet... I'm hoping that upgrading to 0.6.0 will fix my problem, but there is no .deb or repo with the package yet, to my suprise.

---

### Post by fettuohi on 2007-10-30
Anybody know if there is a 3rd party repo up for gutsy yet?

Regards

André

---

### Post by pt123 on 2007-11-02
Is Trevino planning to create a Gutsy repository?

---

