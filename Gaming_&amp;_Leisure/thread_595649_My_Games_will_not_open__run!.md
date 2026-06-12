---
title: "My Games will not open / run!"
date: 2007-10-29
forum: Gaming &amp; Leisure
---

### Post by sgardino on 2007-10-29
So here is my issue.  I'm trying to get some FPS action going on with my Gutsy boot and I'm having some serious issues.  I've installed two games: (America's Army 2.5 and UrbanTerror4) according to directions given at the website and here on the forums.  I've tried installing through terminal and through the GUI and the programs install fine with no errors.  The problem is after I install the games, they will not start.  I've tried executing them from the Menu, Desktop and through Terminal and nothing happens... I've verified that the program's are marked to be ran as an executable, but that hasn't changed anything.  Any thoughts on this issue?  :confused:

---

### Post by weblordpepe on 2007-10-29
Have you tried closing down all internet explorer windows and rebooting the computer? 

Just kidding.
What errors do you get when you try & run the game on the console? And what version of Wine etc do you have?

---

### Post by sgardino on 2007-10-29
I'm not getting any errors, and these are not windows based games.  They're developed for linux.  Let me try to run UT4 and see what error I get

---

### Post by sgardino on 2007-10-29
Ok, so i went to the directory where both the ioUrbanTerror and q3ut4 is installed and through terminal:chmod +x ioUrbanTerror.i386
 ./ioUrbanTerror.i386 

Here is the error:  ./ioUrbanTerror.i386: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by weblordpepe on 2007-10-29
Oh sorry I am half-sleep deprived.

That error is saying that you're missing a SDL library. Go into Synaptic and search for **sdl lib**

You'll find a package there that looks right. You won't need any of the ones that have **-dev** on them, as those are for compiling. You'll want the **lib-sdl** or something.

---

### Post by sgardino on 2007-10-29
RIght now Synaptic indicates that I have Libsdl1.2debian and Libsdl1.2debian-alsa installed... I wonder, is there a specific lib that I need ?

---

### Post by cogadh on 2007-10-29
I usally install libsdl1.2debian-all, just to cover all my bases. I can say for certain that it includes the particular library that error message says you are missing.

---

### Post by sgardino on 2007-10-29
Ok I'll give that a shot... thanks for the help.

---

### Post by sgardino on 2007-10-29
nope.. didn't work... this is where I get stuck at ./ioUrbanTerror.i386
./ioUrbanTerror.i386: error while loading shared libraries: libSDL-1.2.so.0: cannot open shared object file: No such file or directory

---

### Post by cogadh on 2007-10-29
Maybe you should try the install script found here:[http://forums.urbanterror.net/index.php/topic,8165.0.html](http://forums.urbanterror.net/index.php/topic,8165.0.html)
I used it and it installed the game with no problems.

---

### Post by daengbo on 2007-10-29
You should have a library that looks something like this:
/usr/lib/libSDL-1.2.so.0.11.0

in a terminal, type
ls /usr/lib/libSDL*
and post the output here. You may need to make a symlink to the appropriate library.

You may also try running
sudo ldconfig
to update the library cache.

---

### Post by sgardino on 2007-11-01
ok here is the output:

/usr/lib/libSDL-1.2.so.0            /usr/lib/libSDL_mixer-1.2.so.0
/usr/lib/libSDL-1.2.so.0.11.0       /usr/lib/libSDL_mixer-1.2.so.0.2.4
/usr/lib/libSDL_gfx.so.4            /usr/lib/libSDL_net-1.2.so.0
/usr/lib/libSDL_gfx.so.4.9.0        /usr/lib/libSDL_net-1.2.so.0.0.5
/usr/lib/libSDL_image-1.2.so.0      /usr/lib/libSDL_ttf-2.0.so.0
/usr/lib/libSDL_image-1.2.so.0.1.4  /usr/lib/libSDL_ttf-2.0.so.0.6.3
  
Looks like it's there...

---

