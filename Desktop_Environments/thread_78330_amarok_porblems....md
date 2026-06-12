---
title: "amarok porblems..."
date: 2005-10-18
forum: Desktop Environments
---

### Post by questionasker on 2005-10-18
sorry im in a hurry, but after upgrading everything, amarok gives me this error:
```

amaroK could not find any sound-engine plugins. amaroK is now updating the KDE configuration database. Please wait a couple of minutes, then restart amaroK.
If this does not help, it is likely that amaroK is installed under the wrong prefix, please fix your installation using:
$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix=`kde-config --prefix` && su -c "make install"
$ kbuildsycoca
$ amarok
More information can be found in the README file. For further assistance join us at #amarok on irc.freenode.net.
```

any ideas? ill add more info when im back from class.

---

### Post by questionasker on 2005-10-18
i was hoping for a bit of help, oh well...


i used arts before updating and everything ran fine.its a C-media PCI 5-channel card, pretty cheap and basic, but works well normally...

realplayer10 works fine, but none of my other media players work either...
 
any ideas?

---

### Post by skoal on 2005-10-18
"*amaroK could not find any sound-engine plugins*"

I believe I got that error too when I first fired it up.  All you have to do is: Settings > configure Amarok > Engine > and select one.

I personally use the "Xine" engine.  It seems louder and has many options available.  By default, amarok doesn't have any engines associated with it but they're there.

I don't understand the compiling part after that error though.  It's not necessary...

\\//_

---

### Post by Juippisi on 2005-10-18
apt-get install amarok-xine 

I have compiled amarok for myself, now running on 1.3.3 ;-). Works better than the old 1.3.1, or can you get the newest somewhere? For ex. on Kubuntus repos? I'd love to apt-get that :-).

---

### Post by questionasker on 2005-10-18
it wont let me go that far. it exits when i click ok, and it never actually opens the player... :(

---

### Post by skoal on 2005-10-18
oops.  My braincells are deteoriating faster than a beaker full of Plutonium-233.  You _do_ have to use apt-get and install those amarok engines.  There weren't any initially on second thought.

Also, you may waa..want tot..hmm...um...you need, no...um...nevermind...

Where am I anyways???? And what's this doohickey with all the buttons my fingers are pressing? Mommy?!

\\//_

---

### Post by skoal on 2005-10-18
[QUOTE=questionasker]it wont let me go that far. it exits when i click ok, and it never actually opens the player... :([/QUOTE]
Click ok? Juippisi was talking about using Synaptic (or just apt-get from a terminal as he suggested) to install those engines.

Just fire up a terminal (kconsole) and type what he said:

sudo apt-get install amarok-xine

or, if not already installed:

sudo apt-get install synaptic

...and then fire up synaptic under your "System" menu and do a search on "amarok".  Those engines should show up there somewhere in the list.

\\//_

---

### Post by questionasker on 2005-10-18
yeah, i see them, and installed them.

but it still doesnt work...
even after a reboot...

---

### Post by questionasker on 2005-10-18
i even tried unistalling, and installing from source... but that didnt work either-
i got an error about having the wrong qt version...

i dont suppose that could be the trouble...? and if so, how would i go about checking my version and updating? (searching "qt" "qt3" "qt4" does nothing...)

---

### Post by Juippisi on 2005-10-18
Install libdbus-qt-1-1c2, libqt3-headers, libqt3-mt,  libqt3-mt-dev, qt3-dev-tools and try again.

---

### Post by questionasker on 2005-10-18
thanks!

i just didnt know the file names...



we'll see momentarily if this resolves it.

---

### Post by questionasker on 2005-10-18
no dice... same error... :(


edit- ok, let me rephrase-

through apt-get, still the same error...

when i try to compile, now i get a 
"KDE not properly configured, this will fail" error...

so i figured an apt-get dist-upgrade might fix things...
but of course, apt cant find half the updated kde packages from the main breezy repo...

edit again- ok, so this time when i ran apt-get update, it found all the packages, and successfully updated them.
so i rebooted.
amarok stil refuses to work... :(

---

### Post by questionasker on 2005-10-18
ok, so after  making sure everything was updated, i tried to compile again...

when i issue ./configure, it goes about its business until ```
checking for libXext... no
configure: error: We need a working libXext to proceed. Since configure
can't find it itself, we stop here assuming that make wouldn't find
them either.

``` 
comes up... i just updated libxtex6, so i know thats good... what do i do now?


:(

---

### Post by Juippisi on 2005-10-19
```
freedom joonas # apt-cache search libxext
libxext-dev - X11 miscellaneous extensions library (development headers)
libxext6 - X11 miscellaneous extension library
libxext6-dbg - X11 miscellaneous extensions library (debug package)
libxmu-dev - X11 miscellaneous utility library (development headers)
libxmu6 - X11 miscellaneous utility library
libxmu6-dbg - X11 miscellaneous utility library (debug package)
libxmuu-dev - X11 miscellaneous micro-utility library (development headers)
libxmuu1 - X11 miscellaneous micro-utility library
libxmuu1-dbg - X11 miscellaneous micro-utility library (debug package)
xlibs-dev - X Window System client library development files transitional package
```

apt-cache search is your friend ;-). Try installing the -devs, you need those to compile.

---

### Post by questionasker on 2005-10-19
yup, im not THAT much of a newb, i knew to get the devs...

but it still doesnt work...

and now im gettin some error about "not being able to stat "archive.ubunut.com breezy main" or whatever... :(


edit- i have all the packages apt-cache refers to installed.

---

### Post by Juippisi on 2005-10-19
I just realized, that "configure: error: We need a working libXext to proceed. Since configure" means the program itself, not the devs. 

"i have all the packages apt-cache refers to installed." and that's odd.

I have all those libxext -things installed (devs and the others) and I can compile amaroK. 

"and now im gettin some error about "not being able to stat "archive.ubunut.com breezy main" or whatever..." - So, the servers are down for a change. Wait for a while and then try again. Or use something like de.archive.ubuntu.com. When you can connect to repos again, check that you have surely installed _all_ of those, not just the devs. Install also kdebase-dev and it's dependencies, if you haven't already done so.

EDIT: I also have this "x11proto-xext-dev" package installed.

---

### Post by questionasker on 2005-10-19
i just did a dist-upgrade (repos up again) so i know everything is up to date... this is the error i get now, from the CLI...

```
jakey@ubuntu:~ $ amarok
amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
kbuildsycoca running...
Reusing existing ksycoca
kbuildsycoca: ERROR creating database '/var/tmp/kdecache-jakey/ksycoca'!
kbuildsycoca: Wrong permissions on directory? Disk full?

```

---

### Post by crispingatiesa on 2005-10-19
I'm having problems with amarok after installing the nvidia drivers. It was working ok and now when trying to start it just quits. Telling me 

amaroK: [Loader] Starting amarokapp..
amaroK: [Loader] Don't run gdb, valgrind, etc. against this binary! Use amarokapp.
amaroK: [Loader] amarokapp probably crashed!

When calling amarokapp I got:
Segmentation fault

funny if I try to run glxgears I have the same segmentation fault.

The nvida driver works (no problems) and everything was working previously.

Any ideas anybody?

Thanks

---

### Post by questionasker on 2005-10-22
well, i dont know what i did, but it works now...

maybe kde finally rebuilt its engine directory.
:)

---

### Post by mlomker on 2005-10-22
I [posted a how-to]("http://www.ubuntuforums.org/showthread.php?t=80492") for building amaroK from SVN.

---

### Post by nilsb on 2006-01-02
I had trouble starting the xine-engine in amarok too.
My problem was that the sounddeamon gnome uses (esd) blocked the soundcard the xine-engine  was trying to connect to. If your soundcard doesn't support to play more than one sound at a time this happens.

If you use 2 soundcards like me - one for systemsounds and one for music you can use this to get the xine-engine working in amarok:

killall esd

configure amarok now to use the xine-engine and configure your secondary soundcard (fe. hw=1,0 instead of hw=0,0).

when you start the esd now again or restart your gnome session everything should work fine.

---

### Post by dan_hill on 2006-05-16
I'm a debian user, but anyway something like this worked:
rm .kde/share/apps/amarok/xine-config

Good luck!

---

### Post by sinaen on 2006-05-25
Whoa!
I run dapper btw havent found anything about it on a dapper-related thread
tried to install libdbus-qt-1-1c2 libqt3-headers libqt3-mt libqt3-mt-dev qt3-dev-tools
But i already had them.
I have all the engine packages. but when i go into config and engines select xine-engine and then clicks ok and leave the configure menu. it says error cannot load xine-engine void-engine loaded instead. and when i try to play a file it says error no engine loaded, cannot start playback

---

