---
title: "Running MPlayer crashes the X"
date: 2005-05-01
forum: Desktop Environments
---

### Post by aggro on 2005-05-01
When I try to run MPlayer, the X crashes. This started happening after I upgraded from previous Ubuntu release to 5.04 version. The MPlayer is compiled from source (I did make clean, configure, make, make install after upgrading). 

I did also try to use the mplayer that can be installed using apt-get, but that didn't work either. Compiling from source was how I got it to work before upgrade, so that's what I would assume should work also now.

It would be much simpler to try to figure out what is wrong, if only the MPlayer would crash. But since it's the whole X which crashes I have no idea what to do. Any ideas which log files I should look into, or how to fix this? 

I just tried starting mplayer with default configs by calling it: 
mplayer moviefile.avi

---

### Post by bigbangbigbigbang on 2005-05-04
The mplayer coming from ubuntu universe/multiverse is buggy.
Try the mplayer from Marillat (unstable tree), that works fine.
But probably you have to satisfy some dependencies from debian unstable.
I did this and works without any problems.

cheers

---

