---
title: "libSDL.so Error in Auteria"
date: 2010-09-02
forum: Gaming &amp; Leisure
---

### Post by TNAFan on 2010-09-02
Tried installing the game Auteria (from the DJL game installer) anyhow, I got the error of "Could not open SDL library: libSDL.so: cannot open shared object file: No such file or directory".  Everything seems to work though, so I don't know why I am getting the error.  Anyone have any idea why I am getting this or how to fix it?

Edit: Actually it isn't working, it gets to the "loading content" screen and then just sits there.

---

### Post by Naiki Muliaina on 2010-09-02
Not sure how to help with the game manager.

A short n sweet guide to installing Auteria :

[http://www.lostroad.tk/auteria-install-guide-ubuntu-1004.html]("http://www.lostroad.tk/auteria-install-guide-ubuntu-1004.html")

Don't forget if you using 64 bit, make sure you have ia32-libs installed. I think its a 32 bit game. If you need to ask as-well,

sudo apt-get install ia32-libs

Should work.

---

### Post by TNAFan on 2010-09-02
Thanks, but I still get the same error from the terminal

Edit:  Though, it actually loads now, so I am not terribly concerned.  Long as it works I guess.

---

### Post by jtarin on 2010-09-03
> **TNAFan said:**
> Tried installing the game Auteria (from the DJL game installer) anyhow, I got the error of "Could not open SDL library: libSDL.so: cannot open shared object file: No such file or directory".  Everything seems to work though, so I don't know why I am getting the error.  Anyone have any idea why I am getting this or how to fix it?

Edit: Actually it isn't working, it gets to the "loading content" screen and then just sits there.When you get an error like this it is telling you that it cannot find the aforementioned file in its expected place. First look for the file and see if you have it. If you do.....see where the application expects it to be then make a soft link there and it will stop complaining.

---

### Post by TNAFan on 2010-09-03
> **jtarin said:**
> When you get an error like this it is telling you that it cannot find the aforementioned file in its expected place. First look for the file and see if you have it. If you do.....see where the application expects it to be then make a soft link there and it will stop complaining.

How would I do all this?

---

### Post by jtarin on 2010-09-03
Well let's see if you have the file first. In a terminal issue the command ```
sudo updatedb
```this will update the index of all the files on your drive...even windows. If you have not run it before it will take a minute or two. When it has finished then you can use the command ```
locate <filename>
``` to find libSDL.so If its found make note of where it is and  post back....if not then a different search is in order.

---

### Post by TNAFan on 2010-09-04
```
locate libSDL.so
``` simply went back to ~$

---

### Post by jtarin on 2010-09-04
Now issue this command ```
ls -l /usr/lib | grep SDL
```we will see if we can find any instance of the main lib.

---

### Post by TNAFan on 2010-09-04
Came back with

lrwxrwxrwx  1 root root       20 2010-09-03 18:27 libSDL-1.2.so.0 -> libSDL-1.2.so.0.11.3
-rw-r--r--  1 root root   412568 2010-06-09 07:00 libSDL-1.2.so.0.11.3
lrwxrwxrwx  1 root root       25 2010-09-04 01:25 libSDL_image-1.2.so.0 -> libSDL_image-1.2.so.0.8.2
-rw-r--r--  1 root root    46564 2009-11-30 18:12 libSDL_image-1.2.so.0.8.2
lrwxrwxrwx  1 root root       25 2010-09-04 00:58 libSDL_mixer-1.2.so.0 -> libSDL_mixer-1.2.so.0.2.6
-rw-r--r--  1 root root   196268 2009-08-17 20:17 libSDL_mixer-1.2.so.0.2.6
lrwxrwxrwx  1 root root       25 2010-09-04 01:25 libSDL_sound-1.0.so.1 -> libSDL_sound-1.0.so.1.0.2
-rw-r--r--  1 root root   161820 2009-08-18 00:00 libSDL_sound-1.0.so.1.0.2

---

### Post by dfreer on 2010-09-04
Try installing libsdl1.2-dev.
```
sudo apt-get install libsdl1.2-dev
```

---

### Post by TNAFan on 2010-09-04
> **dfreer said:**
> Try installing libsdl1.2-dev.
```
sudo apt-get install libsdl1.2-dev
```

No errors!  Thanks dfreer!

---

### Post by dfreer on 2010-09-04
For future reference:
When you get an error about missing a library, a quick search on [http://packages.ubuntu.com](http://packages.ubuntu.com) for the library will often let you know which package you need to install.

In this case, go to "Search the contents of packages", then type in the library name **libSDL.so**, make sure "packages contain files named like this" radio button is selected.

---

### Post by jtarin on 2010-09-05
Nice Link!

---

### Post by TNAFan on 2010-09-05
> **dfreer said:**
> For future reference:
When you get an error about missing a library, a quick search on [http://packages.ubuntu.com](http://packages.ubuntu.com) for the library will often let you know which package you need to install.

In this case, go to "Search the contents of packages", then type in the library name **libSDL.so**, make sure "packages contain files named like this" radio button is selected.

Awesome link!  Bookmarked!

---

