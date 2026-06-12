---
title: "Problem with eclipse and cairo in Breezy: library not found (although its installed)"
date: 2005-10-21
forum: Desktop Environments
---

### Post by RYX on 2005-10-21
Hello there...

I have a very annoying problem with the Eclipse IDE and a SWT application I'm developing. The app uses the libcairo for drawing antialiased vector paths. Since I upgraded to Breezy, I am not able to run this app from inside Eclipse anymore (using Run As ... > SWT Application). I always get the error: library not found libcairo.so.1 ... but libcairo is definetly installed (although the file libcairo.so.1 is not inside /usr/lib - but libcairo.so.2 is there).

I tried any possible combination of Java/Eclipse installation methods - from installing everything via synaptic/apt-get (which results in an unusable Eclipse installation) to installing everything by hand (which works up to the point my app tries to use cairo). I tried to set the right PATH, JAVA_HOME, ECLIPSE_HOME and LD_LIBRARY_PATH, but it didn't work. 

In another attempt I tried to just add the Eclipse dir (which contains a version of libcairo.so.1 - because Eclipse also uses Cairo) to the LD_LIBRARY_PATH, but this results in another error message when I try to start my app (something like "reference not set" and a line of C-code)... 

I'm moving back to Hoary because I really need to continue my work, but maybe someone out there has some more experience with cairo or eclipse and can figure out where the problem is ... if its an Ubuntu-problem it should be solved 

Thanks in advance ... nice evening everybody!

---

### Post by RYX on 2005-10-22
Good morning out there :)

I spent some more hours on this problem (about the whole night) and I am not done with it, yet. 

The core question is - why is there no libcairo.so.1 in /usr/lib in Breezy?? Cairo is installed by default, so it should be there ... 

... but like mentioned above, there is only a symlink called /usr/lib/libcairo.so.2 which points to /usr/lib/libcairo.so.2.2.3 (I already tried creating another symlink called  libcairo.so.1 - but it didn't change a thing).

In Hoary you had to additionally install libcairo (it was version 0.3.0) - after that, the file /usr/lib/libcairo.so.1 exists.

Maybe this is a problem or bug inside the new Cairo version (Breezy uses 1.0.2, which is quite a big jump from 0.3.0) or it is some kind of "unusual manner" in which Breezy uses Cairo... (or maybe just an improvement and Eclipse's SWT libraries needs to be fixed - I'm using Eclipse 3.1.1?)

I'm no Linux expert at all - maybe I'm just mistaking...

---

### Post by pablete on 2005-12-29
Hi!.. I have a similar problem.
When I start my application, I get this error: 
java: cairo-surface.c:273: cairo_surface_reference: Assertion `surface->ref_count > 0' failed.
my guess is that it's using libcairo.so.2 (that comes with ubuntu ) instead of libcairo.so.1 that comes with eclipse. I tryed setting LD_LIBRARY_PATH but it didn't work...
I'm using eclipse 3.1.0..
Any Ideas?..

TIA!

---

