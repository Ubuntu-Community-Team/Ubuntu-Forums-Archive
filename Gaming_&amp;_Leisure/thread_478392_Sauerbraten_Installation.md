---
title: "Sauerbraten Installation?"
date: 2007-06-19
forum: Gaming &amp; Leisure
---

### Post by try2lickurelbo on 2007-06-19
I really am a noob to Linux, but i've gotten some games installed already.  I've been reading up on it, and I'm desperate for Sauerbraten, it looks so good! ;)
The tutorials I've looked at are really confusing, does anyone know of an easy to read tutorial or, even better, a debian installation for Sauerbraten?

---

### Post by DrMega on 2007-06-19
It really couldn't be easier to install (I know what you mean though, it isn't immediately clear). Decompress the file you downloaded. This will give you a new directory structure for Saurbraten. In there you'll find a file called saurbraten (no extension or anything). Double click it and a dialog will ask if you want to open it or run it in a terminal. Choose run in terminal and off it goes.

You could also set up an application launcher to save you from having to do this every time (a bit like a Windows shortcut).

---

### Post by Butthead on 2007-06-19
Um, didja ever stop to think he might be trying to run it on x86_64 architecture?

That would take it out of the "easy to install" category.

---

### Post by Cappy on 2007-06-19
Actually, I came up with a solution for the problem of running i386 games on amd64. It also solves the problem of missing binaries if you are running an i386 system too.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by noerrorsfound on 2007-06-20
> **Cappy said:**
> Actually, I came up with a solution for the problem of running i386 games on amd64. It also solves the problem of missing binaries if you are running an i386 system too.
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)
For closed source games that's a good solution, but Sauerbraten is open source and compiles without errors on 64-bit. Just type:
```
cd sauerbraten/src
make install
```

---

### Post by Cappy on 2007-06-20
I'm still compilephobic =P

---

### Post by PuppyFromHell on 2007-07-03
> **DrMega said:**
> It really couldn't be easier to install (I know what you mean though, it isn't immediately clear). Decompress the file you downloaded. This will give you a new directory structure for Saurbraten. In there you'll find a file called saurbraten (no extension or anything). Double click it and a dialog will ask if you want to open it or run it in a terminal. Choose run in terminal and off it goes.

You could also set up an application launcher to save you from having to do this every time (a bit like a Windows shortcut).

I too would like sauerbraten but when I decompressed the file all I could find was a file called sauerbraten_unix, and when I clicked that nothing happened.  So I went and ran it in the terminal and got this:

./bin_unix/linux_client: error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory

I really have no idea what it measn besides that it can't find that file.

---

### Post by Cappy on 2007-07-03
if you're running a 32-bit system you can
```
sudo apt-get install libsdl-mixer1.2
```
otherwise it would be best to use getlibs

---

### Post by PuppyFromHell on 2007-07-04
alright I'm not getting that strange error any more but now when I run the scipt in Terminal a black window opens up and then closes after a few seconds (happens from Thunar too), but then the font in Terminal is messed up.  I say font because I assume all the commands work, at least when I typed "exit" it exited Terminal.

---

