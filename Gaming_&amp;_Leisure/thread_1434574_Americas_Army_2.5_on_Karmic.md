---
title: "Americas Army 2.5 on Karmic?"
date: 2010-03-20
forum: Gaming &amp; Leisure
---

### Post by Piro24 on 2010-03-20
I'm trying to play this under Karmic, however, I am getting this error:

```
./armyops-bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
```

Any ideas? I can't seem to figure this one out.

---

### Post by _h_ on 2010-03-20
```
sudo apt-get install libstdc++5
```

Should fix it.

---

### Post by Piro24 on 2010-03-20
That's the first thing that I tried.

```

Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
```

---

### Post by _h_ on 2010-03-20
Weird.

Have you tried looking on the America's Army forums at all? That's where I got the command by googling your error.

---

### Post by Perfect Storm on 2010-03-20
libstdc++5 is obsolete and is no longer part of Ubuntu(9.10) repositories. You can grab libstdc++5 from previous Ubuntu package.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by _h_ on 2010-03-20
Had trouble searching, kept getting blank white page.

But I did find the Jaunty one for anyone having this problem;

[http://packages.ubuntu.com/jaunty/libstdc++5](http://packages.ubuntu.com/jaunty/libstdc++5)


And for all hits: [http://packages.ubuntu.com/search?keywords=libstdc%2B%2B5&searchon=names&suite=all&section=all](http://packages.ubuntu.com/search?keywords=libstdc%2B%2B5&searchon=names&suite=all&section=all)

---

### Post by COden6484 on 2010-03-20
I've been trying to get this running today too on Karmic 64-bit.  I have a symlink set up from libstdc++.so.6 to libstdc++.so.5.  I had to do this to get Enemy Territory to work correctly, which it does.  But with the same symlink set up, I get this when trying to run armyops:

```
./armyops-bin: /usr/lib32/libstdc++.so.5: version `GLIBCPP_3.2' not found (required by ./armyops-bin)
./armyops-bin: /usr/lib32/libstdc++.so.5: version `CXXABI_1.2' not found (required by ./armyops-bin)

```

Any ideas? Thanks!

---

### Post by Piro24 on 2010-03-20
> **Artificial Intelligence said:**
> libstdc++5 is obsolete and is no longer part of Ubuntu(9.10) repositories. You can grab libstdc++5 from previous Ubuntu package.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

Huh, I was about to post saying I had already tried downloading an earlier version from that site (which I had, and it gave me an error saying a newer version  was installed). Anyway, I downloaded [ this file](http://packages.ubuntu.com/jaunty/libstdc++5), and AA will start fine now. 

A bit of tweaking to my video and mouse settings and the game runs practically like I remember it on Windows.


Coden, I suggest you try downloading the 64bit version of the library linked above. Maybe that will help?

---

### Post by Heero_Yuy_X on 2010-03-22
What about 25deploy? I heard it's a bit easier than manual install

---

### Post by jklopez on 2010-03-26
i'm installing aa on 9.10 and all was well i thought but it's been a while and the terminal is still spewing out the same line over and over ,is it still installing or is something wrong the text appering says  loki_setup: Short write on /usr/local/games/armyops/Textures/T-SKY.utx  and it still at it line after line

---

