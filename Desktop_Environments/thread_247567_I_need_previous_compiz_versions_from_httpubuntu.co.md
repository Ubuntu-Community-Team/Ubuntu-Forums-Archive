---
title: "I need previous compiz versions from http://ubuntu.compiz.net/"
date: 2006-08-30
forum: Desktop Environments
---

### Post by McQuaid on 2006-08-30
I know, weird request.  I have an old box with a voodoo3.  2d works fine but I was never able to get opengl working until it was suggested to me to use compiz for the mesa packages.  Lo and behold, it worked, I had opengl working.  Well doing an update, there were new packages available from [http://ubuntu.compiz.net/](http://ubuntu.compiz.net/) and it has messed some things up with regard to opengl again.  

I should have locked the packages but didn't and I already cleared my archive.

These are the files I need:

libdrm-dev (2.0+cvs20060625) 
libdrm2 (2.0+cvs20060625) 
libgl1-mesa (6.5.1-cvs20060628 ) 
libgl1-mesa-dev (6.5.1-cvs20060628 ) 
libgl1-mesa-dri (6.5.1-cvs20060628 ) 
libglu1-mesa (6.5.1-cvs20060628 ) 
libglu1-mesa-dev (6.5.1-cvs20060628 ) 

Someone suggested trying:
aptitude install libgl1-mesa=6.5.1-cvs20060628

but it couldn't find the package.  So I know it's a stretch but does anyone still have the debs of the versions listed above?  Or maybe one of the compiz mirrors retain previous versions?  I couldn't find a way to check the other mirrors.

---

