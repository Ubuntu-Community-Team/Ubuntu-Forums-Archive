---
title: "Doomsday Engine, or Jdoom ?"
date: 2007-07-14
forum: Gaming &amp; Leisure
---

### Post by Christof999 on 2007-07-14
Hello, 

I am running Feisty Fawn, and I would love to play doom. When I ran Windows I ran the doomsday engine. I know its available for Linux, but I haven't found any deb Binaries or Repositories for Feisty.  I know that there is one [http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu](http://eyagi.bpa.nu/eyagi/community-projects/yagisan-s-doomsday-for-debian-ubuntu). But its for Drapper or Breezy. IS there anywhere to get Binaries to easily install Doomsday and Snowberry, or some other Engine that will allow me to choose the Hi-Res textures and 3d models ? 

Ive tried to compile the source but it doesn't seem to work. 

Can someone help me to get Doom working on Ubuntu Feisty ?

Thanks
C.

---

### Post by DoktorSeven on 2007-07-14
I don't use 1.9.0 betas because they've given me nothing but troubles (crash bugs, weird glitches, etc, and the latest one won't even run TNT!).  I did write up a little [guide](http://doktorseven.miskie.net/e107_plugins/forum/forum_viewtopic.php?1) on compiling 1.8.6 though, which has always been wonderfully stable for me.

Edit: forgot to mention I don't use hires or 3d models, but after getting Doomsday/jDoom installed, you should be able to add them, though the method escapes me.  Google should be able to help.

---

### Post by Christof999 on 2007-07-14
Thanks, looks like a good guide. 

How do you do snowberry though ? I really prefer using GUI for everything.

Thanks
C

---

### Post by DoktorSeven on 2007-07-14
I use a custom (minimal) Doomsday launcher I created (also mentioned in the guide) instead of Snowberry.  I can't stand Snowberry's interface, either.

---

### Post by DasCrushinator on 2007-07-14
/usr/bin/ld: cannot find -lXext
collect2: ld returned 1 exit status
rm -f .libs/doomsdayS.o
make[3]: *** [doomsday] Error 1
make[3]: Leaving directory `/home/matthew/deng-1.8.6/Src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/matthew/deng-1.8.6/Src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/matthew/deng-1.8.6'
make: *** [all] Error 2





What did I do wrong :(

Feisty Fawn, up to date.

Creating the symlink did not help.

---

### Post by DasCrushinator on 2007-07-14
Anyone?

---

### Post by DoktorSeven on 2007-07-15
Updated, seems it needs libxext-dev

**sudo apt-get install libxext-dev**

Anytime you compile something and it complains that it can't find **-lsomething** (that's a lowercase L after the dash), drop the dash and the L and place **lib** before and do an **apt-cache search** for it, and install the -dev version of the package to be safe.

(In our case, it was looking for -lXext, drop -l, add lib and get libXext.  **apt-cache search libXext** returns:

```
$ apt-cache search libXext
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

Use the one that's the most similar to the search, with the -dev after it; in our case, it's the first one, libxext-dev.  Doesn't always work but it's worth a try.)

---

### Post by DasCrushinator on 2007-07-15
> **DoktorSeven said:**
> Updated, seems it needs libxext-dev

**sudo apt-get install libxext-dev**

Alright, trying now :)

---

### Post by DasCrushinator on 2007-07-15
Oh thank God, it worked!

---

### Post by DasCrushinator on 2007-07-15
> **DoktorSeven said:**
> Updated, seems it needs libxext-dev

**sudo apt-get install libxext-dev**

Anytime you compile something and it complains that it can't find **-lsomething** (that's a lowercase L after the dash), drop the dash and the L and place **lib** before and do an **apt-cache search** for it, and install the -dev version of the package to be safe.

(In our case, it was looking for -lXext, drop -l, add lib and get libXext.  **apt-cache search libXext** returns:

```
$ apt-cache search libXext
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

Use the one that's the most similar to the search, with the -dev after it; in our case, it's the first one, libxext-dev.  Doesn't always work but it's worth a try.)

Awesome, did not know that!

---

### Post by Shpongled303 on 2007-07-22
> **DoktorSeven said:**
> I use a custom (minimal) Doomsday launcher I created (also mentioned in the guide) instead of Snowberry.  I can't stand Snowberry's interface, either.

First of all I want to thank you for that great Doomsday 1.8.6 installation guide you wrote as well as the gDoomsday front-end. I am pretty sure Doomsday installed OK, and gDoomsday is a great looking front-end.

I'm having a problem though using the front-end.

I pointed the "DOOM II" game to my "doom2.wad" file. Then I hit "Run Doomsday" and I get this error:

> Running Doomsday:
doomsday -game jdoom -file /home/kek/Games/id WADs/doom2.wad  -userdir /home/kek/.doomsday/jdoom -maxzone 256m -window 2>&1

Con_Init: Initializing the console.
SW_Init: Startup message window opened.
Executable: Version 1.8.6 Jul 22 2007 (DGL).
Memory zone: 256.0 Mb.
Parsing configuration files.
W_Init: Init WADfiles.
--- No IWAD has been specified! Important data might be missing. Are you sure you want to continue?
**ERROR** Executable: Version 1.8.6 Jul 22 2007 (DGL).
Memory zone: 256.0 Mb.
Parsing configuration files.
W_Init: Init WADfiles.

W_CheckIWAD: Init aborted.

LoadPlugin: /usr/local/lib/libdpdehread
LoadPlugin: /usr/local/lib/libdpmapload

Any ideas? ?_? Seems like I'm so close to getting it to work! >_<

Thanks,
Sphongled

[EDIT: OK, I found the problem literally seconds after writing this post. It didn't work because the directory I kept my WADs in I entitled "id WADs" -- it really didn't like the space! I changed the name to "id_WADs" and now it works. :)]

P.S. Again, thanks so much for writing this guide... If you didn't write that I might have never been able to get it to work. Maybe someone can put all those steps in a HOWTO Wiki? Great job! Thanks for making my Ubuntu transition less painful. :)

---

