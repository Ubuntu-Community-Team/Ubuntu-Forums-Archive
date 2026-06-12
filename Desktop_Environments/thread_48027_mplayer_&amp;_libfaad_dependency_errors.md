---
title: "mplayer &amp; libfaad dependency errors"
date: 2005-07-10
forum: Desktop Environments
---

### Post by keyshawn on 2005-07-10
Hey, 

I'm trying to install the mplayer-386 package via apt-get and I'm getting an error that I have need to have libfaad2-0 installed...So, when I install libfaad2-0 from apt-get, I get the following error:

 ```
Unpacking libfaad2-0 (from .../libfaad2-0_2.0.0-0.3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libfaad2-0_2.0.0-0.3_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libfaad.so.0.0.0', which is also in package libfaad2
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/libfaad2-0_2.0.0-0.3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

``` 


I have an inkling that this involves Pymusique [the iTunes clone], but the pymusique homepage is down, so I'm a bit stuck there.

---

### Post by ubuntp on 2005-07-19
Remove backports from your sources.list if you got it.

---

### Post by keyshawn on 2005-07-20
I actually was able to figure out a couple days ago. 
Completely removing libfaad [I guess some incarnation of it was installed] and then just reapplied the updates again, and it worked...

However, there's still another problem with mplayer, but that's for a different thread ](*,)

---

