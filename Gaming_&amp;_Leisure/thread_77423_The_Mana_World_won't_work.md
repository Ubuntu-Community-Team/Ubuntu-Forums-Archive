---
title: "The Mana World won't work"
date: 2005-10-16
forum: Gaming &amp; Leisure
---

### Post by Jaivaz on 2005-10-16
When I run it I get the following:

**tmw: error while loading shared libraries: libssl.so.0.9.8: cannot open shared object file: No such file or directory**

Does anybody know how I can fix this? I got TMW to run before by forcing an installation of libssl.so.0.9.8, but because of that I had many problems happen to my computer and I had to do a clean installation. Is there any other way to fix this?

---

### Post by brockjudkins on 2005-10-17
Me too (I'm using TMW's deb repository). It is because ubuntu only gives us libssl0.9.7. Is there a way to fake/fix this dep?

---

### Post by Perfect Storm on 2005-10-17
Try:

```

cd /usr/lib
sudo ln -s libssl.so.0.9.7 /usr/lib/libssl.so.0.9.8

```

---

### Post by brockjudkins on 2005-10-17
That symbolic link worked, thanks!

After doing to same for libcrypto*, I've run into more dep problems:
```

tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by tmw)
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by /usr/lib/libguichan_sdl.so.0)
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by /usr/lib/libguichan.so.0)

```

I have libstdc++.so.6, but something else causing a problem (why GLIBCXX_3.4.6 cant be found). I'd do more research on it but i desperately need some sleep . Again, thanks.

---

### Post by darkwave on 2005-10-17
[QUOTE=brockjudkins]That symbolic link worked, thanks!

After doing to same for libcrypto*, I've run into more dep problems:
```

tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by tmw)
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by /usr/lib/libguichan_sdl.so.0)
tmw: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by /usr/lib/libguichan.so.0)

```

I have libstdc++.so.6, but something else causing a problem (why GLIBCXX_3.4.6 cant be found). I'd do more research on it but i desperately need some sleep . Again, thanks.[/QUOTE]

Same problem for me :(

Help!

ciao,
dw

---

### Post by Perfect Storm on 2005-10-17
Tried?:
```

sudo apt-get install libstdc++6-4.0-dev
sudo apt-get install libstdc++6-dev

```

Edit: Ignore what I wrote. I'm tired it blurred my thoughts.

---

### Post by brockjudkins on 2005-10-18
:( I already had those packages.. 

Looking around, I think it might a conflict between g++3.3 and 3.4.... but I'm still playing with different packages.

---

### Post by MattiasJow on 2005-10-22
I'd like a solution too, please. If anyone knows please tell me. Thx in advance :)

---

### Post by brockjudkins on 2005-10-22
My statement earlier about a clash is based on this thread:

[http://www.linuxquestions.org/questions/history/373052](http://www.linuxquestions.org/questions/history/373052)


I can't, however, recompile with g++3.3 TMW since it came from a deb package.....
or can I?

---

### Post by MattiasJow on 2005-10-22
this is harsh, i changed to ubuntu cus i thought i'd be skipping all the compiling times and few errors, i previously had gentoo, just deleted it, but atleast in that everything did work, tho compiling took some time for the whole system, but i really want to have the mana world to work, and for future version, also i have problems now with compiling Quadra cvs, it just doesnt work. at ./configure stage i get "configure: WARNING: X11 is required and could not be found!
configure: error: Required dependencies missing."
bah.

---

### Post by MattiasJow on 2005-10-23
id like to know how to install glibc 3.4.6 or g++ 3.4.6

---

### Post by slew on 2006-03-11
I'm currently trying to install the new version of [Widelands]("http://sourceforge.net/project/showfiles.php?group_id=40163&package_id=32323&release_id=376020") and I keep getting this error: ./widelands: /usr/lib/libstdc++.so.6: version `GLIBCXX_3.4.6' not found (required by ./widelands). I have installed the libstdc++6.*.dev packages, plus all the dependencies from their readme. I also did the symbolic link that was post a few posts back but I still cant get anywhere with it. Please let me know what more can be done. Thanks!

---

