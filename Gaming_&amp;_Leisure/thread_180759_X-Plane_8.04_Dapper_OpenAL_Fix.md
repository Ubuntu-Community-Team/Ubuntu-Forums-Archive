---
title: "X-Plane 8.04 Dapper OpenAL Fix"
date: 2006-05-22
forum: Gaming &amp; Leisure
---

### Post by oneguynick on 2006-05-22
For those of you running into alutinit errors upon starting the latest x-plane in dapper, try the following:

wget [http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.1.tar.bz2](http://www.swanson.ukfsn.org/loki/loki_compat_libs-1.1.tar.bz2)
tar xfvj loki_compat_libs-1.1.tar.bz2

cd /usr/games/X-Plane 8.04

LD_PRELOAD=/home/nickers/Loki_Compat/libopenal-0.0.so ./X-Plane-athlon-xp

Done. Come to find out, OpenAL as it comes in the dapper repos doesnt have debugging turned on by default. Using the older loki compat libraries skips this. The compat libs are also very handy for running the loki library from a few years back. Be known that this will soon not work with the latest glibc upgrades coming down the pipe. Enjoy this temporary fix!

God Bless,
Nick

---

### Post by tophfisher on 2006-07-09
Nick -

Thanks for the help! Looks like it might not work any more, I get an error after X-Plane starts to load up. I wonder, did you find another fix for this problem?

Thanks!
-Chris

---

### Post by oneguynick on 2006-07-09
I sure haven't played with this since. It was just for my brother. What error are you getting, I maybe of some help!

---

### Post by oneguynick on 2006-07-15
*** glibc detected *** free(): invalid pointer: 0x0dbbc5b0 ***

Is this the error you get now?

---

### Post by theconley on 2006-07-20
> **oneguynick said:**
> Come to find out, OpenAL as it comes in the dapper repos doesnt have debugging turned on by default.

Hey, I'm trying to find OpenAl on the repos.  What should I be looking for?  I can't seem to find it.  I can install it manually, but I wanted to see if I could use Adept.

~Conley

---

### Post by oneguynick on 2006-07-21
libopenal0 is what you are looking for. It is universe though.

---

### Post by theconley on 2006-07-21
My bad, I just checked out the universe thing.

But [I am still having problems]("http://www.ubuntuforums.org/showthread.php?t=220127") if you are interested.

---

### Post by AceB747 on 2006-08-12
I got the openal installed and x-plane is loading up.  Does anyone know how to get the sound to actually work though?

---

### Post by ranpha on 2006-09-26
> **oneguynick said:**
> *** glibc detected *** free(): invalid pointer: 0x0dbbc5b0 ***

Is this the error you get now?

I have this error. also i installed opengl for my ati card flgrxinfo says opengl is on...google earth works with opengl but x-plane doesn't

---

